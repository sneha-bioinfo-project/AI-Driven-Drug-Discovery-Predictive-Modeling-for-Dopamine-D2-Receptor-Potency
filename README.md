# 💊 AI-Driven Drug Discovery: Dopamine D2 Receptor Potency Predictor
### *Machine Learning Pipeline for Bioactivity Classification & Cheminformatics*

## 📌 Executive Summary
This repository features an end-to-end computational pipeline designed to accelerate early-stage drug discovery. By targeting the **Dopamine D2 receptor** (a critical neurological target), I developed a machine learning system that classifies compound potency with high precision. The workflow bridges the gap between raw chemical data (SMILES) and actionable biological insights using state-of-the-art **XGBoost** architecture.

---

## 🚀 Key Technical Milestones

### 1. Automated Bioactivity Sourcing & Cleaning
* **Data Retrieval:** Programmatically sourced bioactivity data from the **ChEMBL Database** (Target: `CHEMBL236`).
* **Quality Control:** Standardized units (nM), removed redundant SMILES, and handled missing values, resulting in a curated library of **562 unique compounds**.
* **Class Stratification:** Applied a threshold of 10,000 nM (10 µM) to define **Active** vs. **Inactive** molecules for supervised learning.

### 2. Cheminformatics & Feature Engineering
* **Feature Extraction:** Leveraged **RDKit** to calculate 9 essential molecular descriptors for every compound.
* **Descriptor Selection:** Focused on properties governing **Lipinski’s Rule of Five**, including:
    * **MW (Molecular Weight)** & **LogP (Lipophilicity)**
    * **TPSA (Topological Polar Surface Area)**
    * **H-Bond Donors/Acceptors** & **Rotatable Bonds**
* **Exploratory Data Analysis (EDA):** Performed correlation mapping to ensure feature independence and interpretability.

### 3. Machine Learning Architecture & Benchmarking
I implemented a comparative model suite to identify the most robust classifier for this imbalanced chemical dataset:

| Model | Accuracy | Precision | F1-Score | ROC-AUC |
| :--- | :--- | :--- | :--- | :--- |
| **XGBoost** | **95.58%** | **1.000** | **0.5455** | **0.7095** |
| Random Forest | 93.81% | 0.6667 | 0.3636 | 0.7875 |
| SVM | 93.81% | 1.000 | 0.2222 | 0.6560 |
| Logistic Regression | 92.92% | 0.000 | 0.0000 | 0.6905 |

**The Win:** XGBoost achieved **100% Precision**, making it a zero-false-positive tool—ideal for minimizing risk in expensive laboratory verification stages.

---

## 🧬 Biological Interpretation (Explainable AI)
The model’s decision-making logic was audited using **Feature Importance**, revealing that the primary drivers of drug potency align with established pharmacological standards:

1. **TPSA (Top Feature):** Lower TPSA predicts superior cell membrane penetration (optimized "sweet spot": 20-130 Å).
2. **Molecular Weight (MW):** Medium weight (160–400 g/mol) molecules showed significantly higher probability of potency.
3. **LogP:** Proved essential for balancing solubility with lipophilicity for receptor binding.

---

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Libraries:** RDKit (Cheminformatics), XGBoost, Scikit-learn, Pandas, Seaborn.
* **Environment:** Google Colab / Jupyter Notebook.
* **Data:** ChEMBL Web Resource Client.

## 📂 Repository Structure
* `Data/`: Raw and processed chemical descriptors.
* `Model/`: Serialized `.pkl` files (XGBoost model, Scaler, and Label Encoder).
* `Results/`: Visualizations of model performance and biological features.
* `AI-Dopamine.ipynb`: Fully documented colab notebook explaining the logic.

---

### 📝 Final "Pro" Note for Recruiters:
> "By achieving **100% Precision** on the test set, this pipeline serves as a reliable 'digital filter,' allowing researchers to prioritize only the most promising candidates for *in vitro* assays, drastically reducing the time-to-discovery for neurological therapeutic agents."
