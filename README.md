# Student Performance Analysis

**M.Tech CSE (Artificial Intelligence) 2026 | Subject Code: MTAI-PE1-20 | Data Preparation and Analysis**

An end-to-end data analysis project using **NumPy, Pandas, Matplotlib, Seaborn and Plotly**. It covers data preprocessing, exploratory data analysis (EDA), static and interactive visualisation, and feature engineering on a student exam-results dataset.

---

## 1. Project description

**Problem statement:** Find out which background factors (gender, parental education, lunch type, test preparation, etc.) are associated with students' exam performance, and prepare the data for further machine-learning work.

**Objectives**
1. Clean and validate the dataset.
2. Explore score distributions and relationships between variables.
3. Visualise the findings with Matplotlib (static) and Plotly (interactive).
4. Engineer meaningful features (encoded and scaled).
5. Summarise findings, recommendations and limitations.

## 2. Dataset

| | |
|---|---|
| **Name** | Students Performance in Exams |
| **Source** | https://www.kaggle.com/datasets/spscientist/students-performance-in-exams |
| **Size** | 1000 rows x 8 columns (CSV) |
| **Columns** | gender, race/ethnicity, parental level of education, lunch, test preparation course, math score, reading score, writing score |

> **License note:** The dataset belongs to its Kaggle author. Check the *License* field on the Kaggle page. If redistribution is not clearly allowed, the CSV is **not** included in this repository. Download it from the link above and place it as described below.

## 3. Libraries used

`numpy`, `pandas`, `matplotlib`, `seaborn`, `plotly` (see `requirements.txt`)

## 4. Repository structure

```
.
├── Student_Performance_Analysis_project.ipynb   # main notebook (Steps 1-9, with outputs)
├── student_performance_analysis.py              # same analysis as a plain Python script
├── requirements.txt
├── README.md
├── StudentsPerformance.csv                      # download from Kaggle (see license note)
└── outputs/
    ├── charts/                                  # PNG (Matplotlib) and HTML (Plotly) charts
    ├── cleaned_students.csv
    ├── feature_engineered_students.csv
    └── before_after_cleaning.csv
```

## 5. How to run

**Option A - Locally**
```bash
git clone <your-repository-url>
cd <repository-folder>
python -m venv venv
venv\Scripts\activate            # Windows  (Linux/Mac: source venv/bin/activate)
pip install -r requirements.txt
# Place StudentsPerformance.csv in this folder, then either:
jupyter notebook Student_Performance_Analysis_project.ipynb     # then Run All
# or
python student_performance_analysis.py
```
> The notebook was run on Google Colab, so it contains two Colab-only cells (Google Drive mount and file upload). When running locally, skip those two cells.

**Option B - Google Colab**
1. Upload the notebook to Colab (File > Upload notebook).
2. Run all cells and upload `StudentsPerformance.csv` when asked.

## 6. Workflow (as per assignment)

| Step | Work done |
|---|---|
| 1 | Dataset collection, problem statement, objectives |
| 2 | NumPy: arrays, indexing, slicing, arithmetic, mean/median/std/min/max/percentiles |
| 3 | Pandas: head/tail, shape, dtypes, summary statistics, missing values, duplicates |
| 4 | Cleaning: column names, dtypes, range validation, duplicates, IQR outlier detection, before/after comparison |
| 5 | EDA: descriptive statistics, group comparisons, correlations, observations |
| 6 | Matplotlib: histogram, bar, line, scatter, box plot, correlation heatmap |
| 7 | Plotly: interactive histogram, scatter, bar chart (and heatmap) |
| 8 | Feature engineering: new features, binary/ordinal/one-hot encoding, z-score and min-max scaling |
| 9 | Findings, recommendations and limitations |

## 7. Key findings

- **Data quality:** no missing values and no duplicates. 12 students are low-score outliers (IQR rule); they are genuine scores, so they were kept and flagged (`is_outlier`).
- **Averages:** math 66.1, reading 69.2, writing 68.1.
- **Correlations:** reading and writing are very strongly correlated (r = 0.95); math correlates about 0.80-0.82 with both.
- **Gender:** males score higher in math; females score higher in reading and writing.
- **Test preparation:** students who completed the course average about 7.6 points higher.
- **Lunch type:** standard-lunch students average about 8.6 points higher than free/reduced-lunch students (the largest gap).
- **Parental education:** higher parental education is generally associated with higher scores.

### Selected visualisations

| Score distributions | Correlation heatmap |
|---|---|
| ![Histograms](outputs/charts/01_histograms.png) | ![Heatmap](outputs/charts/06_correlation_heatmap.png) |

| Test preparation | Reading vs writing |
|---|---|
| ![Bar chart](outputs/charts/02_bar_chart_test_prep.png) | ![Scatter](outputs/charts/04_scatter_reading_writing.png) |

Interactive Plotly charts are saved as HTML files in `outputs/charts/` (download and open them in a browser).

## 8. Engineered features

`total_score`, `average_score`, `writing_reading_gap`, `math_vs_verbal_gap`, `subjects_above_60`, `score_std`, `strongest_subject`, `weakest_subject`, `performance_grade`, `pass_all_subjects`, `high_achiever`, plus encoded columns (`gender_male`, `lunch_standard`, `test_prep_completed`, `parent_edu_level`, one-hot race/ethnicity) and scaled versions of the score columns.

## 9. Limitations

- Only 1000 records from a single, likely synthetic source; results may not generalise.
- No date/time column, so trends over time cannot be studied.
- Race/ethnicity groups are anonymised; socio-economic status is only approximated by lunch type.
- Important factors (study hours, attendance, prior grades) are missing.
- Findings are correlations, not causal effects.

## 10. Author

*Your Name* - M.Tech CSE (AI), 2026 - *Your Roll No / Institute*
