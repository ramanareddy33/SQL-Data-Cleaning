# SQL-Data-Cleaning
This project focuses on cleaning, standardizing, and preparing a global tech layoffs dataset using SQL.
It includes the full end-to-end workflow: staging, deduplication, data standardization, null handling, and preparation for analysis.

Both SQL scripts and raw data are included for transparency and reproducibility.

📁 Project Files
🔹 1. SQL Script

SQL Data Cleaning.sql
Contains all SQL logic used for:

Creating staging tables

Removing duplicates

Standardizing text fields

Cleaning industry, location & company names

Handling nulls

Dropping unnecessary columns


SQL Data Cleaning

🔹 2. Layoffs Dataset (Raw Data)

layoffs.csv — uploaded dataset used for cleaning
Path: /mnt/data/layoffs.csv

Preview of the dataset:
(Loaded directly from the CSV you provided)

company	location	industry	total_laid_off	percentage_laid_off	date	stage	country	funds_raised_millions
Atlassian	Sydney	Other	500	0.05	3/6/2023	Post-IPO	Australia	210
SiriusXM	New York City	Media	475	0.08	3/6/2023	Post-IPO	United States	525
Alerzo	Ibadan	Retail	400	null	3/6/2023	Series B	Nigeria	16
UpGrad	Mumbai	Education	120	null	3/6/2023	Unknown	India	631
Loft	Sao Paulo	Real Estate	340	0.15	3/3/2023	Unknown	Brazil	788
🚀 Data Cleaning Steps (Updated)
1️⃣ Create Staging Tables

Duplicates of the raw table (layoffs → layoffs_staging → layoffs_staging2)

Adds row_num to facilitate duplicate detection

2️⃣ Remove Duplicates

Uses ROW_NUMBER() over:

PARTITION BY company, location, industry, total_laid_off, percentage_laid_off, date, stage, country, funds_raised_millions


Removes all records where row_num > 1

3️⃣ Standardize Text Fields

Examples based on your SQL script:

TRIM(company) to remove whitespace

Merge inconsistent industry names (e.g., Crypto% → Crypto)

Identify and normalize messy location fields

4️⃣ Handle Null & Blank Values

Common issues observed in layoffs.csv:

percentage_laid_off has nulls

Some industries require harmonization

Date column stored as text → convert to DATE

5️⃣ Prepare Dataset for Analysis

Choosing:

Cleaned text fields

Nullable fields handled

Duplicates eliminated

Ready for BI dashboards / ML models / reporting

📊 Dataset Insights (from layoffs.csv)

From the uploaded CSV:

Covers companies across USA, Australia, Nigeria, India, Brazil

Mix of stages: Post-IPO, Series B, Unknown

Industries include: Other, Media, Retail, Education, Real Estate

Total layoffs in sample preview: ~1,835

Percentages laid off included for some firms only

(If you'd like full EDA or charts — I can generate them!)

🛠️ Technologies Used

SQL (MySQL)

Window functions

CTEs

Data profiling techniques

Dataset normalization & cleanup

📌 How to Use

Import layoffs.csv into MySQL as a table named layoffs

Run SQL Data Cleaning.sql step-by-step

Use the final cleaned table (layoffs_staging2) for:

Data analysis

Dashboards (Power BI / Tableau)

Trend insights

Research
