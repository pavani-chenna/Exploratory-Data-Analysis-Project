# Movie Dataset Exploratory Data Analysis (EDA)

## Overview
This project performs *Exploratory Data Analysis (EDA)* on a movie dataset containing over 45,000 records. The analysis involves data cleaning, feature engineering, outlier treatment, and visualizations to understand trends, profitability, and factors affecting movie success.

## Dataset
The dataset contains the following columns:

- adult, belongs_to_collection, budget, genres, homepage, id
- original_language, original_title, overview, release_date
- revenue, runtime, status, vote_average, vote_count
- spoken_languages, production_companies, poster_path, video, tagline

## Data Preprocessing & Feature Engineering

1. *Adult Column*
   - Filtered only True or False values and converted them to boolean.

2. *Collections*
   - Replaced nulls in belongs_to_collection with "No Collection".
   - Extracted collection names into a new column collectionname and dropped belongs_to_collection.

3. *Genres*
   - Applied *one-hot encoding* for each genre column: 1 if the movie belongs to that genre, 0 otherwise.
   - Dropped the original genres column.

4. *Homepage*
   - Created homePagePresent column: 1 if homepage exists, 0 if not.

5. *Budget & Revenue*
   - Converted to integer type and removed null values.
   - Treated outliers using range clipping.
   - Calculated *Profit* = Revenue - Budget and *ROI* = (Revenue - Budget)/Budget, clipped ROI values between -1 and 10.

6. *Runtime*
   - Replaced 0 values with 90 (no movie has 0 runtime).
   - Removed movies with runtime > 220 minutes.

7. *Original Language*
   - Replaced 'en' with 'english' and filled nulls with 'no mentioned'.

8. *Titles & Overview*
   - Dropped duplicate title column and standardized original_title and overview to lowercase and stripped spaces.
   - Filled null overview values with 'no overview'.

9. *Spoken Languages & Production Companies*
   - Counted total languages (TotalLanguages) and number of producers (num_producers).
   - Extracted top 3 producers into Producer1, Producer2, Producer3 columns and dropped production_companies.

10. *Other Columns*
    - Dropped non-numeric or non-informative columns like poster_path, video, tagline.
    - Filled null status values with 'Released'.

11. *Date & Year*
    - Converted release_date to datetime and extracted release_year.

12. *Blockbuster & Genre Count*
    - Created blockbuster column for movies with revenue > 100M.
    - Counted total genres per movie in genre_count.

## Features Created
- collectionname → Name of the collection or 'no collection'.
- One-hot encoded genre columns → 1 if the movie belongs to the genre, 0 otherwise.
- homePagePresent → 1 if homepage exists, 0 otherwise.
- profit → Revenue - Budget
- roi → Return on Investment (Revenue-Budget)/Budget, clipped to [-1,10]
- release_year → Extracted from release_date
- genre_count → Number of genres a movie belongs to
- blockbuster → 1 if revenue > 100M, 0 otherwise
- TotalLanguages → Number of spoken languages
- num_producers → Number of production companies
- Producer1, Producer2, Producer3 → Top 3 producers of the movie

## Analysis & Visualization
- Distribution plots for numeric features: budget, revenue, runtime, vote_average, vote_count, popularity, profit.
- Scatterplots & barplots for:
  - Budget vs Revenue (colored by original language)
  - ROI vs Release Year
  - Runtime vs Vote Average
  - Vote Average vs Profit (colored by genre)
  - Homepage vs Revenue
  - Release Year vs Vote Average (lineplot)
- Countplots for blockbusters and genre distributions.
- Barplots for original language vs vote average.

## Technologies & Tools
- Python, Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook

## How to Run
** Open in Google Colab**
https://colab.research.google.com/drive/1_iNLSEPpsu4e_zffQQ6PUnX-JINdpJ0n?usp=sharing

## visualizations
![image alt](https://github.com/pavani-chenna/Exploratory-Data-Analysis-Project/blob/c097265c43352385d74511e2b3b79dfc17bd24e2/Screenshot%20(5).png)
![image_alt](https://github.com/pavani-chenna/Exploratory-Data-Analysis-Project/blob/e52833670b154d3cf9595723a465ae82faf72d53/Screenshot%20(6).png)
![image_alt](https://github.com/pavani-chenna/Exploratory-Data-Analysis-Project/blob/b4ef506c56fae5c7cc3f5e651bddaad1c2b7bf29/Screenshot%20(7).png)
![image_alt](https://github.com/pavani-chenna/Exploratory-Data-Analysis-Project/blob/dc692bc8b3d6dc948aabe9e83210dd017db24d09/Screenshot%20(8).png)
