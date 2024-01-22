# This line specifies the base Docker image to use. 
# In this case, it's the official Python 3.8 slim image. 
# The slim images are smaller and contain only essential components.
# docker pull python:3.9-slim
FROM python:3.9-slim

# This line sets an environment variable named MICRO_SERVICE with the value /home/app/webapp.
ENV MICRO_SERVICE=/home/app/webapp

# This line creates the directory specified by the MICRO_SERVICE environment variable.
RUN mkdir -p $MICRO_SERVICE

# This line sets the working directory inside the container to the MICRO_SERVICE directory.
WORKDIR $MICRO_SERVICE

# These lines set environment variables for Python:
# PYTHONDONTWRITEBYTECODE is set to 1 to prevent Python from writing pyc files.
# PYTHONUNBUFFERED is set to 1 to ensure that Python's standard output is unbuffered.

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1


# This line upgrades the pip package manager to the latest version.
RUN pip install --upgrade pip

# This line copies the contents of the local src directory into the container at the MICRO_SERVICE directory.
COPY src/ $MICRO_SERVICE

#This line installs Python dependencies listed in the requirements.txt file.
RUN pip install -r requirements.txt

# This line informs Docker that the application inside the container will use port 8501.
EXPOSE 8501

# This line sets the default command to run when the container starts. It runs the Streamlit application using the app.py script.
CMD streamlit run app.py