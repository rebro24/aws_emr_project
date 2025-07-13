# aws_emr_project

The goal of this project was to explore some big data with AWS EMR and PySpark. RedFin's publically available housing market data set was used which was a bit less than 1 GB compressed. 

I had a simple objective, and that was to see what states were selling homes above their average list price.

# Methods

I created an EMR cluster with Spark installed as well as JupyterHub. I tried for a while to use EMR Studio but kept running into IAM-related errors when connecting to the cluster. Right when I thought I had all of the permissions set, EMR Studio decided to just give me generic "An error has occurred" messages which made me decide to just use JupyterHub.

I streamed the RedFin dataset from their S3 bucket into my own S3 bucket. I had to SSH into the primary node and run a bash command to do so since I can't execute bash commands in Jupyter Notebook.

```console
wget -O - https://redfin-public-data.s3.us-west-2.amazonaws.com/redfin_market_tracker/city_market_tracker.tsv000.gz | aws s3 cp - s3://bucket/input/city_market_tracker.tsv000.gz
```

# Forward Looking

A few things that I would like to do when I get the chance:
* Optimize EMR cluster for better execution
* Figure out a way to do the initial load of the data as a step in EMR
* Do some additional data analysis
* Break up JupyterNotebook into steps to be executed by EMR