# Solar-panel-performance-optimization

# ⚡ Solar Panel Efficiency Prediction

As solar energy systems scale up globally, **predicting performance degradation and panel failures** is critical for minimizing downtime and maximizing energy output. This project applies a **stacked regression ensemble** using sensor and environmental data to forecast solar panel efficiency, enabling **predictive maintenance** and operational optimization.

---

## 📁 Dataset Overview

- **Training File**: `data/train.csv` (20,000 rows × 17 columns)  
- **Test File**: `data/test.csv` (12,000 rows × 16 columns)  
- **Sample Submission**: `data/sample_submission.csv`  
- **Target Variable**: `efficiency`  
- **Index**: `id`

### 🧪 Features Used
- **Numerical**: `temperature`, `irradiance`, `humidity`, `panel_age`, `maintenance_count`, `soiling_ratio`, `voltage`, `current`, `module_temperature`, `cloud_coverage`, `wind_speed`, `pressure`
- **Categorical**: `string_id`, `error_code`, `installation_type`

---

## 🧠 Models Used

A **stacked ensemble model** was developed with the following structure:

### 🔁 Base Models
- **Random Forest Regressor** (tuned with GridSearchCV)
- **LightGBM Regressor** (tuned with GridSearchCV)
- **CatBoost Regressor** (tuned with GridSearchCV + early stopping)

### 🧠 Meta Model
- **Ridge Regressor**, trained on out-of-fold (OOF) predictions from base models

---

## 📊 Results

- ✅ **Validation RMSE**: **0.10610**
- ✅ **Mean CV RMSE**: **0.10213**
- ✅ **Custom Score (on validation set)**: **89.38951**
- ✅ **OOF and CV-based stacking strategy used for generalization**
- ✅ Submission generated using predictions on test set

---

## 🚀 Real-World Impact

- **Enables smart monitoring systems** to proactively maintain PV panels.
- **Reduces energy loss** and improves sustainability in large-scale solar farms.
- **Supports intelligent energy grid design** by forecasting panel health trends.

---

## 📦 Installation & Usage

### 1. Clone the repository
```bash
git clone https://github.com/rohankharche34/Solar-panel-performance-optimization.git
cd Solar-panel-performance-optimization
```

### 2. Create and activate a virtual environment (optional but recommended)
```bash
python -m venv venv
source venv/bin/activate  # on Windows use `venv\Scripts\activate`
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

## 🛠 Tech Stack
Python 3.10

Scikit-learn 1.4.2

XGBoost 2.0.3

LightGBM 4.3.0

CatBoost 1.2.3

Pandas, NumPy, Matplotlib, Seaborn
