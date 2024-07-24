# spark-local-deployment

## Step 1: Run your Docker app

## Step 2: Build the image
Command: `docker build -t our-own-apache-spark:3.4.0 -f Dockerfile .`

## Step 3: Run Spark with Docker Compose
Command: `docker-compose up`

## Running a Job
Let's run a job on that cluster (Spark PI example).

### Step 1: Get into the driver container
First, you need to get the driver container name. To get all running containers, run: `docker ps`.
The one running the driver is prefixed by `docker-spark-master`.

### Step 2: Get the Container ID
Get the Container ID (in this example, `78a6fbac7acf`) and get into it:
`docker exec -i -t 78a6fbac7acf /bin/bash`
**Replace `78a6fbac7acf` with your actual container ID.**

### Step 3: Run the Spark job
Navigate to the `/bin` folder and run:
`./spark-submit --master spark://0.0.0.0:7077 --name spark-pi --class org.apache.spark.examples.SparkPi`