# UAS_Analisis-Data-Kompeks-Perminyakan
Pebandingan Model Unsupervised (K-Means, GMM, DBSCAN)
# Unsupervised Machine Learning for Facies Clustering

## 📌 Overview
Repository ini berisi implementasi **unsupervised machine learning** untuk analisis dan clustering data facies reservoir menggunakan dataset `facies_data2.csv`.  
Notebook utama dalam repository ini adalah:
- `Model_Unsupervised_Facies_data2_.ipynb`
Studi ini membandingkan performa **K-Means** sebagai baseline dengan **DBSCAN** sebagai model unsupervised alternatif, serta menggunakan **PCA** untuk visualisasi hasil clustering.
---
## 📂 File Structure
* Model_Unsupervised_Facies_data2_.ipynb
* Facies_data2.csv
* README.md

---

## 🧠 Methods Used

### 1. Data Preprocessing
- Seleksi fitur numerik dari dataset
- Penghapusan kolom label facies (jika tersedia) karena pendekatan unsupervised
- Normalisasi data menggunakan **StandardScaler** untuk menghindari dominasi fitur tertentu

---

### 2. Unsupervised Learning Models

#### 🔹 K-Means Clustering (Baseline)
- Digunakan sebagai model pembanding utama
- Jumlah cluster ditentukan berdasarkan asumsi jumlah facies
- Efektif untuk data dengan struktur klaster yang relatif jelas dan homogen

---

#### 🔹 DBSCAN (Density-Based Spatial Clustering)
- Tidak memerlukan jumlah cluster di awal
- Mengelompokkan data berdasarkan kepadatan
- Mampu mendeteksi **noise / outlier**
- Cocok untuk data dengan distribusi dan kepadatan tidak seragam

---

#### 🔹 Gaussian Mixture Model (GMM)
- Model probabilistik berbasis distribusi Gaussian
- Mengasumsikan data berasal dari campuran beberapa distribusi normal
- Menghasilkan **soft clustering**, yaitu satu data dapat memiliki probabilitas ke beberapa cluster
- Cocok untuk data dengan overlap antar klaster

---

## 📊 Model Evaluation

Karena metode yang digunakan adalah **unsupervised learning**, evaluasi model dilakukan tanpa menggunakan label aktual.  
Beberapa metrik evaluasi yang digunakan dalam notebook adalah:

### 🔹 Silhouette Score
- Mengukur seberapa mirip suatu data dengan klasternya sendiri dibandingkan klaster lain
- Nilai berada pada rentang **-1 hingga 1**
- Semakin mendekati 1, kualitas klaster semakin baik

Silhouette Score digunakan untuk:
- K-Means
- DBSCAN (dengan mengabaikan data noise)
- GMM (menggunakan hasil hard clustering dari probabilitas tertinggi)

---

### 🔹 Akaike Information Criterion (AIC) dan Bayesian Information Criterion (BIC) – khusus GMM
- Digunakan untuk mengevaluasi **model probabilistik**
- Mengukur trade-off antara:
  - Kualitas model
  - Kompleksitas model
- Nilai **AIC/BIC yang lebih rendah** menunjukkan model yang lebih optimal

AIC dan BIC digunakan untuk:
- Menentukan jumlah komponen Gaussian yang paling sesuai
- Membandingkan beberapa konfigurasi GMM

---

## 📉 Dimensionality Reduction (PCA)
- **Principal Component Analysis (PCA)** digunakan untuk mereduksi dimensi data menjadi 2 komponen utama
- PCA hanya digunakan untuk **visualisasi**, bukan untuk training model
- Membantu interpretasi hasil clustering dalam ruang dua dimensi

---

## 📊 Visualization
Visualisasi mencakup:
- Clustering K-Means pada ruang PCA
- Clustering DBSCAN pada ruang PCA
- Clustering GMM pada ruang PCA
- Perbandingan pola klaster antar model

Visualisasi ini memberikan gambaran perbedaan karakteristik klaster yang dihasilkan oleh masing-masing algoritma.

---

## 📈 Results Summary
- **K-Means** menghasilkan klaster yang relatif seragam namun sensitif terhadap outlier
- **DBSCAN** mampu mendeteksi noise dan klaster berbasis kepadatan
- **GMM** mampu menangkap distribusi klaster yang saling tumpang tindih melalui pendekatan probabilistik

Evaluasi menggunakan Silhouette Score serta AIC/BIC menunjukkan bahwa setiap model memiliki keunggulan tergantung karakteristik data.

---

## 📝 Conclusion
Studi ini menunjukkan bahwa:
- K-Means cocok sebagai baseline untuk data terstruktur
- DBSCAN unggul dalam mendeteksi outlier
- GMM memberikan fleksibilitas tinggi dalam menangani klaster yang overlap

Pemilihan algoritma unsupervised harus disesuaikan dengan:
- Distribusi data
- Keberadaan noise
- Kompleksitas struktur klaster

---

## 🛠 Requirements
Library yang digunakan:
- pandas
- numpy
- matplotlib
- scikit-learn

Python versi 3.8 atau lebih baru direkomendasikan.

---

## ▶️ How to Run
1. Clone repository ini
2. Pastikan file `facies_data2.csv` berada dalam direktori yang sama
3. Jalankan `Model_Unsupervised_Facies_data2_.ipynb` menggunakan Jupyter Notebook atau Jupyter Lab

---

## 👤 Author
**Rendy Pradana Renaldy**  
Teknik Perminyakan  
Unsupervised Machine Learning – Facies Analysis

---
