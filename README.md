# 🏠 Bengaluru House Price Prediction

A complete end-to-end machine learning project for predicting residential property prices in Bengaluru (Bangalore), India. The project features a full data pipeline (loading → cleaning → feature engineering → model training) and an interactive frontend built entirely with Python (`ipywidgets`) inside a Jupyter Notebook.

---

## 📂 Dataset

| Detail | Info |
|---|---|
| **Name** | Bengaluru House Data |
| **Kaggle Link** | [https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data](https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data) |
| **Local file** | `Bengaluru_House_Data.csv` |
| **Rows** | ~13,000 listings |
| **Columns** | `area_type`, `availability`, `location`, `size`, `society`, `total_sqft`, `bath`, `balcony`, `price` |

---

## 📋 Project Description

The goal of this project is to accurately predict house prices (in Indian Rupees — Lakhs) for properties in Bengaluru based on features such as location, total area, number of bedrooms (BHK), bathrooms, balconies, and area type.

The project is structured as a single Jupyter Notebook (`SouvikMaity_HousePricePrediction.ipynb`) that integrates:

- **Backend** — data loading, cleaning, feature engineering, training/evaluation of five regression models, and a `predict_price()` inference function.
- **Frontend** — an interactive `ipywidgets` UI embedded in the notebook that allows users to input property details and receive instant price estimates, along with exploratory data analysis charts.

---

## 🛠️ Technologies Used

| Layer | Technology |
|---|---|
| Language | Python 3.9+ |
| Data manipulation | `pandas`, `numpy` |
| Machine Learning | `scikit-learn` (Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting) |
| Model persistence | `joblib` |
| Visualisation | `matplotlib`, `seaborn` |
| Frontend / UI | `ipywidgets`, `IPython.display` |
| Runtime | Jupyter Notebook / JupyterLab |

---

## 🗂️ Project Structure

```
.
├── Bengaluru_House_Data.csv       # Raw dataset
├── House_Price_Prediction.ipynb   # Main notebook (backend + frontend)
├── Requirements.txt               # Python dependencies
├── README.md                      # This file
├── Project_Documentation.docx    # Full project documentation
│
# Generated after running the notebook:
├── house_price_model.pkl          # Trained best-performing model
├── scaler.pkl                     # StandardScaler for linear models
├── label_encoder_area.pkl         # LabelEncoder for area_type
├── feature_columns.pkl            # Ordered list of feature column names
├── location_list.pkl              # List of known locations
└── area_type_list.pkl             # List of area type classes
```

---

## ⚙️ Setup & Run Instructions

### 1. Prerequisites

- Python 3.9 or higher
- `pip` package manager

### 2. Clone / Download the project

```bash
# If using git
git clone <your-repo-url>
cd bengaluru-house-price-prediction

# Or simply download and extract the project folder
```

### 3. (Recommended) Create a virtual environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r Requirements.txt
```

### 5. Place the dataset

Ensure `Bengaluru_House_Data.csv` is in the **same directory** as the notebook.

### 6. Launch Jupyter Notebook

```bash
jupyter notebook
# or for JupyterLab:
jupyter lab
```

### 7. Run the notebook

Open **`SouvikMaity_HousePricePrediction.ipynb`** and choose:

- **Kernel → Restart & Run All** to execute all cells sequentially, OR
- Run each cell (Shift + Enter) from top to bottom.

After all cells have executed, the interactive price predictor UI will appear at the bottom of the notebook.

### 8. Use the UI

1. Select a **location** (type to search or choose from the dropdown).
2. Choose an **Area Type**.
3. Enter **Total Sq.Ft**, **BHK**, **Bathrooms**, and **Balconies**.
4. Click **Predict Price** to see the estimated price.
5. Click **Show EDA Charts** to explore data visualisations.

---

## 📊 Models Trained

| Model | Notes |
|---|---|
| Linear Regression | Baseline |
| Ridge Regression | L2 regularisation (α=10) |
| Lasso Regression | L1 regularisation (α=1) |
| Random Forest | 100 estimators, best overall R² |
| Gradient Boosting | 100 estimators |

The model with the **highest R²** on the test set is automatically selected and used for predictions.

---

## 🔑 Key Information

- Prices are predicted in **Indian Rupees (Lakhs)**. The UI also displays the equivalent in **Crores**.
- Locations with fewer than 10 listings are grouped as `"other"` to avoid overfitting on rare categories.
- Outliers are removed per-location using ±1 standard deviation on **price per sq.ft**.
- The `total_sqft` field supports range values (e.g. `2100-2850`) — these are averaged automatically.
- All model artefacts (`.pkl` files) are saved to the project root after the notebook is executed, enabling future inference without retraining.

---

## 📄 License

This project is released for educational purposes. The dataset is publicly available on Kaggle under its respective licence.
