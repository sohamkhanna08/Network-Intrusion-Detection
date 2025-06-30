# Network Intrusion Detection using Machine Learning

## 📚 Introduction

In the modern world, networks face constant threats from intrusions, malicious actors, and cyberattacks. Detecting these threats quickly and accurately is crucial for ensuring the security and integrity of any digital infrastructure.

This project implements a **Network Intrusion Detection System (NIDS)** using supervised machine learning techniques. The goal is to analyze network traffic data and classify connections as **normal** or **anomalous** (attack), providing a foundation for further development into real-time intrusion prevention systems.

---

## 📂 Dataset Choice

I used the **Network Intrusion Detection dataset** ([available on Kaggle](https://www.kaggle.com/datasets/sampadab17/network-intrusion-detection)), a widely recognized benchmark dataset for intrusion detection research. The dataset simulates a military network environment subjected to various attacks and normal traffic, capturing different types of TCP/IP connections.

**Key Characteristics:**

* Each record represents a single TCP connection between a source and destination IP.
* 41 features per record, including 38 continuous or discrete numeric features and 3 categorical features (`protocol_type`, `service`, `flag`).
* Each record is labeled as either **normal** or as an **attack type** (e.g., DoS, Probe, R2L, U2R).

---

## ⚙️ Project Workflow

### 1️⃣ Data Collection & Exploration

* Load dataset using `pandas`.
* Inspect columns, missing values, and data types.
* Explore distributions of categorical features and continuous variables.

### 2️⃣ Data Preprocessing

* **Handle Missing Values:** Drop or impute rows with missing entries (if any).
* **Encode Categorical Variables:** Convert `protocol_type`, `service`, and `flag` into numerical values using `LabelEncoder` or `factorize`.
* **Feature Engineering:** Generate derived features (optional) or remove redundant ones based on correlation analysis.
* **Scaling:** Normalize continuous features to ensure even distance measurement for KNN.

### 3️⃣ Model Selection

We chose the **K-Nearest Neighbors (KNN)** algorithm due to its simplicity and interpretability:

* Works well with small to medium-sized feature spaces.
* Easy to update with new data.
* Effective baseline for classification tasks with mixed categorical and numeric features.

### 4️⃣ Model Training & Evaluation

* **Train/Test Split:** 80% training, 20% testing using `train_test_split` with a fixed random state for reproducibility.
* **Training:** Fit the KNN model with `n_neighbors=5`.
* **Evaluation Metrics:**

  * **Accuracy:** Overall correct predictions.
  * **Confusion Matrix:** Shows distribution of predictions across true classes.
  * **Precision, Recall, F1-Score:** Performance for each class.

### 5️⃣ Visualization

* Correlation heatmap of numeric and encoded categorical features using `seaborn`.
* Confusion matrix plotted as a heatmap to visualize classification performance.

---

## 📊 Results

This heatmap shows correlation among features.
![image](https://github.com/user-attachments/assets/50e216bc-fb07-469b-86ad-2c0d7cc03ee2)

Confusion matrix shows classification performance across classes.
![image](https://github.com/user-attachments/assets/ae64e1e9-4479-40aa-93e2-704aa8e26d43)

---

## 🛠️ Libraries & Tools Used

* `pandas` for data manipulation
* `numpy` for numerical operations
* `scikit-learn` for machine learning algorithms and evaluation metrics
* `matplotlib` & `seaborn` for data visualization

---

## 🚀 Future Scope

* Use advanced models like Random Forest, SVM, or Deep Learning (LSTM) for better temporal pattern analysis.
* Integrate with real-time network packet sniffers (e.g., Wireshark) for live detection.
* Deploy as a REST API microservice using Flask or FastAPI.
* Implement alerting system to notify security teams of high-risk connections in real-time.

---

## 📜 References

* [Network Intrusion Detection dataset](https://www.kaggle.com/datasets/sampadab17/network-intrusion-detection)
* scikit-learn documentation
* seaborn & matplotlib documentation

### ⭐ **If you found this helpful, consider giving this repo a star!**
