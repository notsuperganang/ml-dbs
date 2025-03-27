# 🛡️ Bank Transaction Fraud Detection System

![Fraud Detection Banner](https://img.shields.io/badge/🔍-FRAUD%20DETECTION-red?style=for-the-badge) 
![Python](https://img.shields.io/badge/python-3.8+-blue.svg?style=flat&logo=python) 
![Pandas](https://img.shields.io/badge/pandas-1.3.5-150458.svg?style=flat&logo=pandas) 
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0.2-F7931E.svg?style=flat&logo=scikit-learn) 
![Clustering](https://img.shields.io/badge/Clustering-Agglomerative-yellow) 
![Classification](https://img.shields.io/badge/Classification-XGBoost-green)

## 📑 Daftar Isi
- [Tentang Project](#-tentang-project)
- [Dataset](#-dataset)
- [Struktur Project](#-struktur-project)
- [Metode](#-metode)
- [Hasil dan Temuan](#-hasil-dan-temuan)
- [Setup dan Instalasi](#-setup-dan-instalasi)
- [Penggunaan](#-penggunaan)
- [Kredit](#-kredit)

## 🔍 Tentang Project

Project ini mengembangkan sistem deteksi kecurangan (fraud detection) dalam transaksi perbankan menggunakan metode **unsupervised clustering** dan **supervised classification**. Tujuan utamanya adalah mengidentifikasi pola-pola transaksi mencurigakan secara otomatis dengan akurasi tinggi.

Dalam dunia keuangan digital, kerugian akibat fraud mencapai miliaran dolar setiap tahunnya. Sistem deteksi otomatis menjadi sangat krusial untuk memproteksi nasabah dan institusi keuangan. Project ini mendemonstrasikan pendekatan machine learning yang kuat dan efektif untuk tantangan tersebut.

## 📊 Dataset

Dataset mencakup **2,512 transaksi bank** dengan 16 fitur penting:

- **TransactionID, AccountID**: Pengenal unik untuk transaksi dan akun
- **TransactionAmount**: Nilai moneter transaksi
- **TransactionDate**: Waktu terjadinya transaksi
- **TransactionType**: Kategori 'Credit' atau 'Debit'
- **Location**: Lokasi geografis transaksi
- **DeviceID** & **IP Address**: Identifikasi perangkat dan jaringan
- **MerchantID**: ID pedagang
- **AccountBalance**: Saldo setelah transaksi
- **PreviousTransactionDate**: Waktu transaksi terakhir
- **Channel**: Kanal transaksi (ATM, Online, Branch)
- **CustomerAge**: Usia pemegang akun
- **CustomerOccupation**: Pekerjaan (Doctor, Engineer, Student, Retired)
- **TransactionDuration**: Durasi transaksi dalam detik
- **LoginAttempts**: Jumlah percobaan login

## 📁 Struktur Project

```
.
├── [Clustering]_Submission_Akhir_BMLP_Ganang_Setyo_Hadi.ipynb  # Notebook untuk clustering
├── data
│   ├── processed  # Data yang telah diproses
│   │   ├── after-clustering.csv
│   │   ├── after-eda.csv
│   │   ├── after-feature-selection.csv
│   │   ├── after-preprocessed.csv
│   │   └── scaled_for_classification.csv
│   └── raw
│       └── raw-data.csv  # Data asli
├── [Klasifikasi]_Submission_Akhir_BMLP_Ganang_Setyo_Hadi.ipynb  # Notebook untuk klasifikasi
└── README.md
```

## 🔬 Metode

Project ini menggunakan pendekatan dua tahap untuk deteksi fraud:

### 1️⃣ Unsupervised Learning (Clustering)
- **Feature Engineering** yang ekstensif dengan mengekstrak fitur seperti:
  - Transaction Velocity
  - Amount Percentile
  - Amount Ratio to Average
  - Time-Based Features (Is_Weekend, Is_Late_Night)
  - Potential Fraud Score
- **Agglomerative Clustering** dengan average linkage (Silhouette Score: 0.71)
- Identifikasi cluster transaksi mencurigakan (0.44% dari total)

### 2️⃣ Supervised Learning (Classification)
- Menggunakan hasil clustering sebagai label untuk training model klasifikasi
- **Random Forest** dan **XGBoost** untuk klasifikasi transaksi
- Hyperparameter tuning untuk meningkatkan performa
- Feature importance analysis untuk interpretabilitas model

## 📈 Hasil dan Temuan

### Clustering
- Berhasil mengidentifikasi **2 cluster utama** dengan Silhouette Score **0.71**
- **Cluster 0 (Transaksi Mencurigakan)**: 11 transaksi (0.44%)
  - Jumlah transaksi rata-rata: **$1,615.84** (5.5x lebih besar dari transaksi normal)
  - Potential Fraud Score: **0.44** (8.8x lebih tinggi)
  - Login Attempts: Rata-rata **2.00** (1.8x lebih banyak)

- **Cluster 1 (Transaksi Normal)**: 2,501 transaksi (99.56%)
  - Jumlah transaksi rata-rata: **$291.80**
  - Potential Fraud Score: **0.05**
  - Login Attempts: Rata-rata **1.12**

### Klasifikasi
- **Random Forest**: Akurasi 100%, F1-Score 100%
- **XGBoost**: Akurasi 99.60%, F1-Score 99.67%
- **Feature Importance**: Amount_Percentile, TransactionAmount, dan Potential_Fraud_Score menjadi prediktor terkuat

> Model XGBoost menunjukkan sedikit trade-off dengan precision kelas fraud sebesar 50%, namun tetap memiliki recall yang tinggi. Ini menunjukkan model masih memerlukan penyesuaian untuk mengurangi false positives.

![Feature Importance Chart](https://img.shields.io/badge/⚠️-Visualisasi%20dapat%20dilihat%20pada%20notebook-orange)

## 🔧 Setup dan Instalasi

1. Clone repository ini:
```bash
git clone https://github.com/ganangsetyohadi/bank-fraud-detection.git
cd bank-fraud-detection
```

2. Buat dan aktifkan virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. Install dependensi:
```bash
pip install -r requirements.txt
```

4. Jalankan Jupyter Notebook:
```bash
jupyter notebook
```

## 💻 Penggunaan

1. Buka notebook `[Clustering]_Submission_Akhir_BMLP_Ganang_Setyo_Hadi.ipynb` untuk melihat proses clustering
2. Buka notebook `[Klasifikasi]_Submission_Akhir_BMLP_Ganang_Setyo_Hadi.ipynb` untuk melihat proses klasifikasi
3. Data yang telah diproses tersedia di folder `data/processed/`

## 🏆 Kredit

Project ini dikembangkan oleh:

**Ganang Setyo Hadi**  
📧 Email: ganangsetyohadi@gmail.com  
🔗 GitHub: [ganangsetyohadi](https://github.com/notsuperganang)

---

*Project ini diselesaikan sebagai bagian dari Submission "Membangun Proyek Machine Learning" pada modul "Belajar Machine Learning untuk Pemula" di program CodingCamp yang diselenggarakan oleh Bank DBS bersama Dicoding.*