CodeAlpha Data Analytics Internship — Task 2: Exploratory Data Analysis

Exploratory Data Analysis (EDA) on the Titanic passenger dataset, performed as part of the CodeAlpha Data Analytics internship.

Objective

Understand the structure and quality of the dataset, then use statistics and visualization to test whether commonly assumed survival factors — sex, class, age, family size — actually hold up in the data, rather than assuming they do.

Dataset

891 Titanic passengers (training set), from the official Kaggle Titanic competition — "Titanic: Machine Learning from Disaster." Included locally in data/train.csv so the notebook runs without needing a Kaggle account.

Tools used
Tool	Purpose
Python 3	Core language
pandas	Loading, cleaning, grouping, aggregating tabular data
numpy	Numeric operations
matplotlib / seaborn	Visualization — distributions, bar charts, heatmaps
scipy.stats	Hypothesis testing (chi-square, t-test) — statistical rather than purely visual validation
Jupyter Notebook (via Google Colab)	Code, explanation, and output together in one file
Method
Ask meaningful questions before touching the data
Structure check — shape, dtypes, summary statistics
Missing-data audit
Cleaning — targeted imputation, not blanket drop/fill
Univariate analysis — one variable at a time
Bivariate analysis — survival vs. sex, class, age
Feature engineering — family_size, then a class × sex multivariate view
Outlier detection — IQR method on fare
Hypothesis testing — chi-square tests of independence, Welch's t-test
Key insights
Overall survival rate: 38.4%.
Sex was the strongest predictor: women survived at 74.2% vs. 18.9% for men (χ² = 260.72, p ≈ 1.2 × 10⁻⁵⁸).
Class mattered too, monotonically: 1st class 63.0% → 2nd 47.3% → 3rd 24.2% (χ² = 102.89, p ≈ 4.6 × 10⁻²³).
Age alone was not statistically significant (Welch's t-test, p = 0.082 at α = 0.05) — "women and children first" holds for women, but age by itself doesn't separate survivors from non-survivors.
Small families (2–4 members) outsurvived both solo travelers (30.4%) and large families (5+).
Fare has 116 upper-bound outliers (13.0% of passengers) by the IQR method.
Cabin (77% missing) was dropped; Age (20% missing) was imputed using the median within each class+sex group, not one global average.
Repo structure
CodeAlpha_ExploratoryDataAnalysis/
├── CodeAlpha_ExploratoryDataAnalysis.ipynb
├── data/
│   └── train.csv
└── README.md
How to run
bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook CodeAlpha_ExploratoryDataAnalysis.ipynb

Or open directly in Google Colab.

CodeAlpha Data Analytics Internship — Task 2
