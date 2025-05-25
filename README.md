# 🌦️ Real-Time Weather Sentiment Analysis Pipeline

This project implements a real-time data pipeline that ingests weather data from an API, stores it in Amazon S3, streams it via Kafka, processes it using PySpark for sentiment analysis, and visualizes the results with Power BI, using Snowflake as the analytics layer.


## 🔧 Technologies Used

- **Weather API** (data source)
- **Amazon S3** (raw and processed storage)
- **EC2** (Python producer to Kafka)
- **Apache Kafka** (streaming platform)
- **Apache Spark (PySpark)** (stream processing and sentiment analysis)
- **Snowflake** (data warehouse)
- **Power BI** (dashboard/visualization)


## 🔄 Data Flow

```text
[Weather API]
      ↓
[Amazon S3 Bucket: to_processed/]
      ↓
[EC2 Python Script → Kafka Topic]
      ↓
[PySpark Streaming: Sentiment Analysis]
      ↓
[Amazon S3 Bucket: processed/sentiments/]
      ↓
[Snowflake Data Warehouse]
      ↓
[Power BI Dashboard]




## 📂 Project Files

- [lambda_kafka.py](lambda_kafka.py) — AWS Lambda function code that fetches weather from the Weather API and pushes data to Kafka on EC2.
- [glue.py](glue.py) — AWS Glue script that reads weather data from Kafka, performs sentiment analysis, and writes results to S3.
- [snowflake.sql](snowflake.sql) — SQL script used to create tables and load data into Snowflake from S3.
