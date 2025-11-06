# hello-apache-airflow


> Airflow is the open source standard for orchestrating ETL/ELT data pipelines.

Source: <https://airflow.apache.org/use-cases/etl_analytics/>

## Set up environment

Source: https://airflow.apache.org/docs/apache-airflow/stable/installation/installing-from-pypi.html

Using uv to create a project:

```bash
uv init --python 3.13 hello-apache-airflow
cd hello-apache-airflow
```

Set the Airflow home:

```bash
export AIRFLOW_HOME=$(pwd)/.airflow
```

Set environment variables and install:

```bash
AIRFLOW_VERSION=3.1.2
PYTHON_VERSION="$(uv run python -c 'import sys; print(f"{sys.version_info.major}.{sys.version_info.minor}")')"
CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
uv pip install "apache-airflow[async,postgres,google]==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
```

Initalizing Airflow and run Airflow Standalone:

```bash
uv run airflow standalone
```

Access the [Airflow UI](http://localhost:8080). Password can be found in terminal or in [this file](.airflow/simple_auth_manager_passwords.json.generated).

If you want to remove the default examples, you can do the following:

- Set the `load_examples = False` in [airflow.cfg](.airflow/airflow.cfg).
- Reset the db using this command: `uv run airflow db reset`
- Restart airflow standalone: `uv run airflow standalone`

## Sources

Install using uv:
<https://engineergatitu.medium.com/installing-apache-airflow-with-uv-a-modern-python-package-management-approach-1ba20cd1eb44>

Quick start:
<https://airflow.apache.org/docs/apache-airflow/stable/start.html#quick-start>

Using TaskFlow API:
<https://airflow.apache.org/docs/apache-airflow/stable/tutorial/taskflow.html>

Nice writeup on how to load data into BigQuery from an API using Apache Airflow:
<https://medium.com/merkle-data-technology/orchestrate-airflow-pipeline-to-fetch-data-from-an-api-and-upload-it-to-bigquery-f93990bad723>
