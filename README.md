# Rock-Paper-Scissors Classification Project 🪨📄✂️

## 📚 Deskripsi Proyek
Proyek ini membangun sistem klasifikasi gambar menggunakan **Deep Learning** dengan arsitektur **Transfer Learning** berbasis **MobileNetV2**. Model ini mampu mengklasifikasikan gambar ke dalam tiga kategori: **Rock**, **Paper**, dan **Scissors**. 

Model yang dilatih telah berhasil diintegrasikan ke dalam aplikasi backend berbasis **FastAPI** dan frontend **Streamlit**, sehingga dapat menerima gambar dan memberikan hasil prediksi secara real-time.

![image](https://github.com/user-attachments/assets/eb794960-da96-4e98-b759-66e345cb7194)


---

## 🛠️ Teknologi yang Digunakan
- **TensorFlow / Keras** — Untuk membangun dan melatih model klasifikasi gambar.
- **FastAPI** — Untuk membangun backend REST API.
- **Streamlit** — Untuk membangun antarmuka pengguna.
- **Uvicorn** — Sebagai ASGI server untuk menjalankan FastAPI.
- **PIL (Pillow)** — Untuk memproses gambar.
- **NumPy** — Untuk manipulasi data numerik.
- **scikit-learn** — Untuk evaluasi model (classification report, confusion matrix).

---

## 📊 Hasil Evaluasi Model

Hasil evaluasi model menunjukkan performa yang baik pada dataset test:

### Classification Report
```
              precision    recall  f1-score   support

       paper     0.9787    0.9892    0.9840        93
        rock     0.9915    0.9915    0.9915       117
    scissors     0.9920    0.9841    0.9880       126

    accuracy                         0.9881       336
   macro avg     0.9874    0.9883    0.9878       336
weighted avg     0.9881    0.9881    0.9881       336
```

### Confusion Matrix
![Confusion Matrix](![image](https://github.com/user-attachments/assets/7043dbec-ec59-414d-9524-d4d680d272e1))
Model mencapai akurasi **98.81%** pada dataset test, dengan performa yang sangat baik di ketiga kelas. Dari confusion matrix, dapat dilihat bahwa hanya terdapat beberapa kesalahan prediksi, dimana:
- 1 gambar paper salah dikenali sebagai scissors
- 1 gambar rock salah dikenali sebagai paper
- 1 gambar scissors salah dikenali sebagai paper dan 1 lagi sebagai rock

---

## 📂 Struktur Folder Proyek
```
project-root/
├── backend/
│   └── main.py         # Kode backend FastAPI
│   └── requirements.txt
├── frontend/
│   └── app.py          # Aplikasi Streamlit
│   └── requirements.txt          
├── model/
│   └── best_transfer.h5 # Model hasil training yang disimpan
├── dataset/
│   ├── rock/
│   ├── paper/
│   └── scissor/
└── README.md
```

---

## 🚀 Langkah Penggunaan

### 1. Clone Repository
```bash
git clone https://github.com/furqanx/Tugas-Pembelajaran-Mesin.git
cd Tugas-Pembelajaran-Mesin
```

### 2. Siapkan Environment Python
Disarankan menggunakan **Python 3.9–3.11**. Buat environment baru, lalu install dependencies:
```bash
python -m venv venv
source venv/bin/activate  # Untuk Linux/Mac
# atau
venv\Scripts\activate  # Untuk Windows

pip install -r requirements.txt
```

### 3. Download Dataset
Unduh dataset Rock-Paper-Scissors dari Kaggle:
🔗 [Rock-Paper-Scissors Dataset – Kaggle](https://www.kaggle.com/datasets/drgfreeman/rockpaperscissors)

Setelah download dan ekstrak:
- Susun dataset ke dalam folder:
  ```
  dataset/
      rock/
      paper/
      scissor/
  ```

### 4. Jalankan Backend dan Frontend
Jalankan backend FastAPI:
```bash
cd backend
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```
Server akan berjalan di `http://localhost:8000/`.

Jalankan frontend Streamlit:
```bash
cd frontend
streamlit run main.py
```
Aplikasi akan berjalan di `http://localhost:8501/`.

---

## 📸 Screenshots

### Tampilan Aplikasi
![Application Interface](![Hasilmodelgunting](https://github.com/user-attachments/assets/5b2f277d-54b2-4f92-a302-3aa95c5e5f1b))

### Prediksi "Rock"
![Hasilmodelbatu](https://github.com/user-attachments/assets/29d55c54-6f2b-4b83-ad1d-fb29e6a17dc4)

### Prediksi "Paper"
![Paper Prediction](![Hasilmodelkertas](https://github.com/user-attachments/assets/12adb8df-0e6f-4cd7-a353-cf5daa9ad0de))

### Prediksi "Scissors"
![Scissors Prediction](![Hasilmodelgunting](https://github.com/user-attachments/assets/f4d84841-a98c-40de-bcf7-b38e9820d406))

---

## 📝 Proses Pengembangan

### Transfer Learning dengan MobileNetV2
Model ini menggunakan arsitektur MobileNetV2 yang telah pre-trained pada dataset ImageNet sebagai feature extractor. Dengan memanfaatkan transfer learning, model dapat mencapai performa tinggi meskipun dengan dataset yang relatif kecil.

### Data Augmentation
Untuk meningkatkan robustness model, diterapkan teknik data augmentation seperti:
- Random flip horizontal
- Random rotation (±10%)
- Random zoom (±10%)
- Random contrast adjustment (±10%)

Augmentasi ini hanya diterapkan pada training set untuk memperkaya variasi data, sementara validation dan test set tetap dalam bentuk aslinya.

### Early Stopping
Untuk mencegah overfitting, diterapkan teknik Early Stopping yang akan menghentikan proses training jika tidak ada peningkatan performa pada validation set selama 3 epoch berturut-turut.

---

## 🔍 Insight dan Tantangan

### Insight
- Model mencapai konvergensi dengan cepat berkat penggunaan transfer learning.
- Performa model sangat baik di ketiga kelas dengan f1-score di atas 97%.
- Preprocessing yang konsisten antara training dan inferensi sangat penting untuk performa yang optimal.

### Tantangan
- Memastikan konsistensi preprocessing antara pipeline training dan inferensi.
- Mengintegrasikan model dengan backend FastAPI dan frontend Streamlit.
- Menangani kondisi ketika input tidak sesuai dengan kategori yang diharapkan (threshold confidence).

---

## 📋 Kontributor
- [Nama Anda] - [Link GitHub Anda]

---

## 📜 Lisensi
Proyek ini dilisensikan di bawah [MIT License](LICENSE).
