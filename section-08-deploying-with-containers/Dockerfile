FROM python:3.9.4

# Create the user that will run the app
RUN adduser --disabled-password --gecos '' ml-api-user

# establishing working directory
WORKDIR /opt/house-prices-api

# setting variable
ARG PIP_EXTRA_INDEX_URL

# copy the files needed to the docker image
ADD ./house-prices-api /opt/house-prices-api/
# upgrading pip and then installing requirements
RUN pip install --upgrade pip
RUN pip install -r /opt/house-prices-api/requirements.txt

# enabling permissions to make sure that the user is able to run the bash script
RUN chmod +x /opt/house-prices-api/run.sh
RUN chown -R ml-api-user:ml-api-user ./

USER ml-api-user

# exposing the port needed to run uvicorn
EXPOSE 8001

# execute command to run the bash script
CMD ["bash", "./run.sh"]
