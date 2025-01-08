## Setting up the project

Begin by setting up the project structure. For this, we will use the following folder structure:

```plaintext
etl-example/
├── config/
│   ├── __init__.py
│   └── db_config.py
├── data/
│   ├── output/
│   ├── processed/
│   └── raw/
├── docs/
│   └── flowcharts/
│       └── etl_flowchart.md
├── etl/
│   ├── extract/
│   │   ├── __init__.py
│   │   ├── extract.py
│   ├── load/
│   │   ├── __init__.py
│   │   ├── load.py
│   ├── sql/
│   ├── transform/
│   │   ├── __init__.py
│   │   ├── transform.py
│   └── __init__.py
├── notebooks/
│   └── exploratory_analysis.ipynb
├── scripts/
│   ├── __init__.py
│   └── run_etl.py
├── tests/
│   ├── __init__.py
├── .env
├── .env.dev
├── .env.test
├── .gitignore
├── README.md
├── requirements-setup.txt
├── requirements.txt
└── setup.py
```

Once this is done, set up your production, test and development environments and make sure to install the required dependencies.

## Installing the required dependencies.

Make sure you have downloaded and installed PostgreSQL on your machine. 
Then create a Python virtual environment and install the required packages:

```bash
python3 -m venv .venv
source .venv/bin/activate       # On Windows, use .venv\Scripts\activate
pip install -r requirements-setup.txt
```

```bash
pip install python-dotenv psycopg2 pandas pytest pytest-cov pytest-mock pytest-postgresql flake8 sqlfluff
```

Freeze the requirements to the `requirements.txt` file:

```bash
pip freeze > requirements.txt
```

Run the project setup script to install the project as a package:

```bash
pip install -e .
```

## Setting up the databases

Create the development and test source databases by running the following commands on the terminal (given you have successfully installed Postgres!):

```bash
psql -U postgres -c "CREATE DATABASE etl_demo_dev_source;"
psql -U postgres -c "CREATE DATABASE etl_demo_test_source;"
```

## Running the tests

A unit test has been created for the config.db_config module.  This test checks that the correct values are loaded from the `.env` files.

To run the test, use the following command:

```bash
run_tests unit
```

This command will run the unit tests and output the results to the console.

## Running the ETL pipeline 

## Additional information 