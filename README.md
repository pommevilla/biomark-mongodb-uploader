# GERMS Biomark MongoDB Uploader

This pipeline uploads Biomark readings and associated metadata to the GERMS MongoDB.

## Getting started

### Create your `.env` file 

1. Get access to the MongoDB database (ask Paul for help)
2. Create an `.env` file by copying and renaming `.env.example`.
3. Fill in your MongoDB password and username in `.env`. 
    * `.env` is under `gitignore`, so your private credentials won't be uploaded to git in the event you pushed to the repo. 

### Creating the conda environment

1. Install [conda](https://docs.conda.io/en/latest/), the Python package manager. I actually recommend using [mamba](https://github.com/mamba-org/mamba), but you can use whichever you like.
2. Create the environment by entering `conda env create -f environment.yml`. If you are using `mamba`, instead type `mamba env create -f environment.yml`. This will set up the virtual environment with all the required packages for the pipeline.

## Database schema

This script will upload files to the `all_biomark_data` database of the GERMS mongodb. In that database, there are currently two collections:

* `biomark_runs` - this contains top-level information about datasets that have been uploaded to the database. The information is:
    * Dataset name
    * Person uploading
    * Project name
* `run_data` contains the actual data from the `biomark_run`. This contains the actual row data from the processed biomark data. 

The two databases are related by the dataset name field.
