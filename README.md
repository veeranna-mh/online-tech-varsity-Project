# 📊 Scaler Clustering Analysis

## 📌 Problem Statement
Scaler (an online tech learning platform) wants to **profile learners and identify patterns** based on their:
- Company
- Job Role
- Experience
- Compensation (CTC)

The goal is to **cluster similar learners** and derive **actionable business insights**.

---

## 📁 Dataset
- Source: `scaler_kmeans.csv`
- Key Features:
  - `company_hash` – anonymized company
  - `job_position` – role/title
  - `orgyear` – employment start year
  - `CTC` – current compensation
  - `ctc_updated_year` – last salary update
  - `email_hash` – unique learner identifier

---

## ⚙️ Approach

### 1. Data Preprocessing
- Handled missing values (KNN / mode imputation)
- Removed duplicates
- Cleaned text using regex
- Created new feature: **Years_of_Experience**
- Removed invalid records (future years, unrealistic experience)

---

### 2. Manual Clustering
Created business-driven segments using:
- **Company + Job Role + Experience**

Generated flags:
- **Designation** → relative salary within same role & experience  
- **Class** → relative salary within same role  
- **Tier** → relative salary within company  

Used these to answer:
- Top / Bottom employees
- Top companies
- Top roles per company

---

### 3. Unsupervised Clustering
- Feature encoding (One-hot / Label encoding)
- Standardization
- **K-Means clustering**
- **Agglomerative clustering (sample-based due to memory limits)**
- Elbow method for optimal clusters
- PCA / t-SNE for visualization

---

## 📊 Key Insights
- Salary strongly correlates with **experience**, but varies significantly across companies
- Same job roles have **wide compensation variation across companies**
- Certain companies consistently fall into **higher salary tiers**
- Manual clustering provided **more interpretable business insights** than pure ML clustering

---

## 🚀 Challenges Faced
- High cardinality in categorical features → huge dimensionality after encoding
- Memory issues with:
  - Hierarchical clustering
  - PCA / t-SNE on full dataset
- Data quality issues:
  - Missing job roles
  - Invalid `orgyear`

---

## 🧠 Learnings
- Importance of **data cleaning before clustering**
- Trade-off between **interpretability (manual clustering)** and **scalability (ML clustering)**
- Handling **high-dimensional data**
- Practical limitations of clustering algorithms on large datasets

---

## 🛠️ Tools & Libraries
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn

---

## 📎 Conclusion
This project demonstrates how clustering techniques (manual + ML-based) can be used to:
- Understand learner segmentation
- Benchmark salaries
- Identify high-value companies and roles
