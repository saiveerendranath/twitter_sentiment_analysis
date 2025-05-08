# Twitter Sentiment Pipeline

This project implements a full pipeline for processing and analyzing Twitter sentiment. Below is an overview of the directory structure.

## Directory Structure

```plaintext
twitter-sentiment-pipeline/
│
├── README.md                         # Project overview and setup instructions
├── requirements.txt                  # Python dependencies
├── .env                              # Environment variables (do not commit)
├── docker-compose.yml                # For local orchestration (Kafka, Airflow, etc.)
├── .gitignore
│
├── config/                           # Centralized configs for all services
│   ├── logging.yaml
│   ├── kafka_config.json
│   ├── airflow_config.json
│   └── db_config.yaml
│
├── ingestion/                        # Streaming or batch data ingestion
│   ├── kafka_producer.py             # Tweets → Kafka
│   ├── twitter_stream.py             # Tweepy stream client
│   └── ingestion_airflow_dag.py      # Airflow DAG for ingestion
│
├── raw_data/                         # Sample or debug raw data (local dev only)
│   └── sample_tweets.json
│
├── processing/                       # Data transformation & sentiment analysis
│   ├── clean_transform.py            # Cleaning and formatting
│   ├── sentiment_scorer.py           # Sentiment analysis logic (VADER/TextBlob)
│   ├── spark_job.py                  # Spark pipeline for ETL
│   └── processing_airflow_dag.py     # Airflow DAG for processing
│
├── warehouse/                        # Data warehouse integration
│   ├── schema.sql                    # Target table schemas
│   ├── load_to_warehouse.py          # Final loader script
│   └── warehouse_airflow_dag.py      # Orchestrate load jobs
│
├── orchestration/                    # Airflow / Prefect / Dagster setup
│   ├── airflow/
│   │   ├── dags/
│   │   │   └── __init__.py
│   │   └── docker/
│   │       └── Dockerfile
│   └── scripts/
│       └── start_airflow.sh
│
├── models/                           # Sentiment models (if ML-based)
│   └── transformer_model.py
│
├── storage/                          # Scripts for storing to cloud (S3/GCS)
│   ├── s3_uploader.py
│   └── cloud_storage_dag.py
│
├── api/                              # Optional REST API to serve results
│   ├── app.py                        # Flask or FastAPI app
│   └── routes.py
│
├── dashboard/                        # Optional dashboard
│   └── streamlit_app.py
│
├── docker/                           # Docker-related files
│   ├── Dockerfile-ingestion
│   ├── Dockerfile-processing
│   ├── Dockerfile-api
│   └── Dockerfile-airflow
│
└── terraform/                        # Infrastructure as Code
    └── main.tf
