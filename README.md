# BLACK-FRIDAY-SALES-ANALYSIS

# 🛍️ Black Friday Sales — Exploratory Data Analysis

Exploratory Data Analysis (EDA) on a Black Friday retail transactions dataset, focused on understanding what drives **Purchase amount** — the target variable — across customer demographics and product categories.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-3776AB)
![Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📌 Overview

This project analyzes **550,068 transaction records** from a retail store's Black Friday sale, covering **5,891 unique customers** and **3,631 unique products**. The goal is to explore how customer attributes (gender, age, occupation, city, marital status) and product attributes (product categories) relate to the amount spent per transaction.

The analysis includes full data preprocessing, univariate analysis, and bivariate analysis (each feature vs. `Purchase`), backed by visualizations.

---

## 🎯 Objectives

- Understand the structure, quality, and completeness of the dataset
- Study the distribution of `Purchase` and detect outliers
- Clean and preprocess the data — handle missing values, encode categorical variables, rename fields
- Perform **Univariate Analysis** on individual features
- Perform **Bivariate Analysis** of each feature against `Purchase`
- Visualize key patterns (histograms, boxplots, bar charts, pie charts, heatmaps)
- Summarize insights relevant to marketing and inventory decisions

---

## 📂 Dataset

| Column | Description | Type |
|---|---|---|
| `User_ID` | Unique identifier for each customer | Identifier |
| `Product_ID` | Unique identifier for each product | Identifier |
| `Gender` | Gender of the customer (M / F) | Categorical |
| `Age` | Age group of the customer (binned range) | Categorical (Ordinal) |
| `Occupation` | Masked occupation code | Categorical (Numeric) |
| `City_Category` | City category the customer resides in (A/B/C) | Categorical |
| `Stay_In_Current_City_Years` | Years the customer has stayed in the current city | Categorical (Ordinal) |
| `Marital_Status` | 0 = Single, 1 = Married | Categorical (Binary) |
| `Product_Category_1` | Masked primary product category | Categorical (Numeric) |
| `Product_Category_2` | Masked secondary product category (may be absent) | Categorical (Numeric) |
| `Product_Category_3` | Masked tertiary product category (may be absent) | Categorical (Numeric) |
| **`Purchase`** | **Purchase amount — Target Variable** | Numeric (Continuous) |

> **Note:** `Occupation`, `Product_Category_1`, `Product_Category_2`, and `Product_Category_3` are **masked** — their original categorical labels were already converted to numeric codes by the data provider.

---

## 🗂️ Project Structure

```
black-friday-sales-eda/
│
├── Black_Friday_Sales.csv                  # Raw dataset (not included — see below)
├── Black_Friday_Sales_EDA.ipynb            # Main analysis notebook (Colab-ready)
├── Black_Friday_Sales_Project_Report.docx  # Full written project report
└── README.md
```

> The raw CSV is not committed to this repo due to size. See [Getting Started](#-getting-started) for how to add it.

---

## 🧹 Data Preprocessing

- Checked basic statistics, missing values, and unique value counts
- **Missing values:** `Product_Category_2` (31.6% missing) and `Product_Category_3` (69.7% missing) — filled with `0` (meaning "no sub-category applicable")
- Dropped unnecessary identifier columns: `User_ID`, `Product_ID`
- Renamed columns for clarity (e.g. `Stay_In_Current_City_Years` → `Stay_Years`)
- Mapped categorical columns to integers using `map()`:
  - `Gender`: F → 0, M → 1
  - `City_Category`: A → 0, B → 1, C → 2
  - `Age` (ordinal): 0-17 → 0, 18-25 → 1, 26-35 → 2, 36-45 → 3, 46-50 → 4, 51-55 → 5, 55+ → 6
  - `Stay_In_Current_City_Years`: '4+' → 4, cast to integer

---

## 📊 Key Findings

| Analysis | Insight |
|---|---|
| **Purchase distribution** | Right-skewed; mean ≈ 9,264, median = 8,047, range 12–23,961 |
| **Outliers** | Only 0.49% of transactions (IQR method) — genuine high-value purchases, not errors |
| **Gender** | 75.3% of transactions are male; males also spend more per transaction on average (₹9,437.53 vs ₹8,734.57) |
| **Age** | 26–35 age group is the most active (39.9% of transactions); avg. purchase is fairly stable across age groups |
| **City Category** | City B has the most transactions, but **City C has the highest average purchase** (₹9,719.92) |
| **Marital Status** | Minimal effect on purchase amount (Single: ₹9,265.91 vs Married: ₹9,261.17) |
| **Product Category** | Strongest driver of purchase value — Category 10 averages ₹19,675.57 despite low transaction volume, while high-volume categories (1, 5, 8) have lower average value |

📄 Full breakdown, tables, and business interpretation available in [`Black_Friday_Sales_Project_Report.docx`](./Black_Friday_Sales_Project_Report.docx).

---

## 📈 Visualizations Included

- Purchase distribution (histogram + boxplot) and outlier detection
- Count plots: Gender, Age, City Category, Marital Status, Stay Years, Occupation
- Bivariate boxplots & average-purchase bar charts for every feature vs. `Purchase`
- Pie charts: City Category distribution, Gender distribution
- Correlation heatmap across encoded features
- Multi-variable views: Age × Gender vs Purchase, Age × City Category vs Purchase
- Top 10 most frequently purchased products

---

## 🛠️ Tools & Technologies

- **Python 3**
- **Pandas** & **NumPy** — data manipulation
- **Matplotlib** & **Seaborn** — visualization
- **Google Colab** — notebook execution environment

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/shahanansari-creator/black-friday-sales-eda.git
cd black-friday-sales-eda
```

### 2. Add the dataset
Place `Black_Friday_Sales.csv` in the project root (or upload it when prompted inside the notebook).

### 3. Run the notebook
- **Google Colab (recommended):** open `Black_Friday_Sales_EDA.ipynb` in Colab and run all cells — it will prompt a file upload if the CSV isn't already present.
- **Locally / Jupyter:**
```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Black_Friday_Sales_EDA.ipynb
```

---

## 🔮 Future Scope

- Build a regression model (Linear Regression, Random Forest, XGBoost) to predict `Purchase`
- Customer segmentation via clustering for targeted marketing
- Market basket analysis on product category co-purchases
- Time-based trend analysis if transaction timestamps become available

---

## 👤 Author

**Mohd Shahan Ansari**
- GitHub: [@shahanansari-creator](https://github.com/shahanansari-creator)
- LinkedIn: [mohd-shahan-ansari](https://www.linkedin.com/in/mohd-shahan-ansari-100479259/)

---

## 📄 License

This project is open-sourced under the [MIT License](LICENSE).
