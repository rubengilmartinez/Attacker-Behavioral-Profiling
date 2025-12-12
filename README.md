# Attacker Behavioral Profiling in SSH Honeypots

This project develops a complete behavioral profiling framework for SSH attackers using raw Cowrie honeypot logs.  
Through large-scale preprocessing, feature engineering, and a multi-density clustering algorithm, the system identifies distinct attacker profiles such as automated bots or human operators but it is not the key information which the system provides us, with a deep analysis of the different clusters we have been able to identify not only the profile of the attackers but also their intention in each session.

The project is fully reproducible end-to-end through the provided Jupyter notebooks.

---

## 📂 Repository Structure



    Attacker-Behavioral-Profiling/
    │
    ├── DATASETS/
    │ ├── cleaned_parquet_datasets/ # Reduced sample datasets (Parquet)
    │ └── raw_dataset/ # Small sample of raw files used for testing
        └── attacker_behavioral_profiles_dataset_3.0.csv
        └── attacker_profiles_FINAL_DATASET.csv # Final session-level feature matrix
        └── executed_commands.csv # For a depper analysis
    ├── images_reports/ # Figures generated during experimentation
    │
    ├── gifs_reports/ # Animations generated during experimentation
    │
    ├── notebooks/
      ├── data_cleaning_pipeline.ipynb # Full preprocessing pipeline
      ├── unsupervised_approach.ipynb # K-Means and baseline exploration
      ├── hdbscan_advanced_final_algorithm.ipynb # Multi-density DBSCAN method



> **Note:** Only a small subset of Parquet files is included due to size constraints.  
> Full datasets can be downloaded from the CyberLab Honeynet dataset (Zenodo).

---

## ⚙️ Installation & Requirements

This project requires **Python 3.12** and the following libraries:

- numpy  
- pandas  
- dask  
- scikit-learn  
- matplotlib  
- seaborn  
- plotly

(Any standard Python environment with these packages is sufficient.)

---

## 🚀 How to Run the Project

All notebooks are **fully executable end-to-end**.

### Recommended execution order:

1. **`data_cleaning_pipeline.ipynb`**  
   - Loads raw logs  
   - Cleans and normalizes events  
   - Reconstructs sessions  

2. **`unsupervised_approach.ipynb`**  
   - Seed-based heuristic labeling  
   - K-Means exploratory clustering  
   

3. **`hdbscan_advanced_final_algorithm.ipynb`**  
   - Multi-density DBSCAN (Levels 1–3)  
   - Final behavioral clustering  

All resulting datasets and cluster labels are exported inside the `notebooks/` folder.

---

## 📊 Project Workflow (ASCII Diagram)


    Raw Cowrie Logs
            ↓
    Data Cleaning & Normalization (Dask)
            ↓
    Session Reconstruction (per-session timelines)
            ↓
    Feature Engineering
            ↓
    Iterative DBSCAN Clustering (Levels 1–3)
            ↓
    Consolidation of Behavioral Groups
            ↓
    Final Attacker Profiles



---

## 🔍 Key Findings

Based on the final distribution of attacker behavioral groups:

- **Massive Automated Bots** dominate, accounting for the majority of all SSH intrusion attempts.
- **IoT/Mirai-like Bots** form the second-largest category, highlighting the prevalence of IoT-targeted malware activity.
- **Medium-density and semi-human patterns** (e.g., Script Kiddies) appear only in small, infrequent clusters.
- **Skilled Human Operators** and **Anomalous Outliers** are extremely rare but remain highly significant from a security and threat-analysis standpoint.

---

## 🧪 Outputs Generated

- Fully cleaned **event-level dataset**  
- **Session-level feature matrix**  
- Final **cluster labels** for every attacker session  
- Multiple figures summarizing behavioral groups  
- Complete academic report (included in this repo)

---

## ⚠️ Known Limitations

- Only a limited subset of the full dataset is included due to size restrictions.  
- Attackers may detect the honeypot environment, altering their behavior.  
- Lack of ground-truth labels requires behavioral interpretation via unsupervised learning.  
- Clustering results depend on algorithmic parameters and dataset characteristics.

---

## 👥 Authors

- **Rubén Gil Martínez**  
- **Jorge Mejías Donoso**  
- **Guillermo López Pérez**  
Cybersecurity — University of Bologna, Italy  

---

## 📄 License

This project is licensed under the **MIT License**.

