# Capstone_2 - Analisis Mikrotrans Jakarta: Gratis, Tapi Untuk Siapa?

**Tools**: Python & Tableau  
**Visualisasi**: Python (Matplotlib, Seaborn, Plotly, Folium) & Tableau  
**Dataset**: Transaksi Mikrotrans Jakarta (Transjakarta)

---

## Daftar Isi

1. [Latar Belakang dan Masalah](#1-latar-belakang-dan-masalah)
2. [Pembersihan & Pemahaman Data](#2-pembersihan--pemahaman-data)
3. [Analisis Data](#3-analisis-data)
4. [Kesimpulan dan Rekomendasi](#4-kesimpulan-dan-rekomendasi)
5. [Visualisasi Tableau](#5-visualisasi-tableau)

---

## 1. Latar Belakang dan Masalah

Mikrotrans hadir sebagai layanan transportasi gratis dari Transjakarta, dengan tujuan menjangkau area pemukiman padat dan wilayah tanpa akses bus besar. Namun, muncul pertanyaan:

> **"Gratis, tapi untuk siapa?"**

Apakah akses terhadap Mikrotrans sudah adil dan merata di seluruh Jakarta?

### Rumusan Masalah:
- Siapa pengguna dominan layanan Mikrotrans?
- Kapan dan bagaimana pola perjalanan dilakukan?
- Wilayah mana yang tidak memiliki halte Mikrotrans?
- Apakah terjadi ketimpangan akses atau perilaku gagal tap out berdasarkan demografi?

---

## 2. Pembersihan & Pemahaman Data

Data utama: `Transjakarta.csv`  
Isi data:
- Informasi pengguna (usia, jenis kelamin)
- Waktu tap-in dan tap-out
- Jenis moda transportasi
- Lokasi halte (lat/lon)
- Status tap-out (berhasil/gagal)

Langkah yang dilakukan:
- Mengimpor data transaksi Mikrotrans dari file `.csv`
- Mengecek dan menangani nilai kosong
- Konversi kolom waktu (`tapInTime`, `tapOutTime`) ke format datetime
- Membuat fitur baru: `tripDuration`, `tapInHour`, `weekday`, `date` `age`, `ageGroup`, `transportationType` dan `tapOutStatus`
- Konversi koordinat dan penggabungan spasial dengan data kecamatan

---

## 3. Analisis Data

### Segmentasi & Perilaku Pengguna:
**- Langkah yang dilakukan:**
- Membagi pengguna berdasarkan usia dan jenis kelamin
- Visualisasi: Bar chart dan distribusi pengguna
**- Insight:** 
- Kelompok usia dewasa awal mendominasi
- Penggunaan tertinggi saat weekday & jam sibuk pagi–sore

### Waktu & Durasi:
**- Langkah yang dilakukan:**
- Analisis waktu padat (jam sibuk) dan rata-rata durasi perjalanan
- Uji statistik Kruskal-Wallis untuk melihat perbedaan signifikan antar jam
**- Insight:**
- Rata-rata durasi meningkat saat peak hour
- Mikrotrans banyak digunakan pada saat weekday

### Akses Wilayah:
**- Langkah yang dilakukan**
- Membuat GeoDataFrame halte dari koordinat tap in dan tap out
- Spatial join dengan shapefile kecamatan (GeoJSON)
- Menghitung jumlah halte per kecamatan
- Identifikasi kecamatan blankspot (tanpa halte Mikrotrans)
**- Insight:**
- Kecamatan dengan jumlah halte tertinggi: Jakarta Timur
- Wilayah minim halte (blankspot): Mampang Prapatan.

### Gagal Tap Out:
**- Langkah yang dilakukan**
- Mengukur proporsi gagal tap out pada berbagai kelompok
- Uji Mann-Whitney U untuk melihat perbedaan berdasarkan jam

**- Insight:**
- Kelompok usia lebih senior cenderung gagal lebih banyak
- Tingkat gagal tap out cukup tinggi pada moda Mikrotrans
- Kelompok usia senior cenderung lebih banyak gagal

---

## 4. Kesimpulan dan Rekomendasi

### Kesimpulan:
- **Akses Mikrotrans belum merata**
- **Pengguna aktif terkonsentrasi di wilayah tertentu**
- **Masih terjadi banyak gagal tap out**

### Rekomendasi:
- Pemerataan armada & halte Mikrotrans
- Evaluasi sistem tap-out & inklusi pengguna lansia
- Fokus ekspansi ke wilayah yang belum terlayani

---

## 5. Visualisasi Tableau

Untuk mendukung narasi data, analisis ini juga divisualisasikan menggunakan Tableau:

🔗 **[Klik untuk melihat Dashboard Tableau](https://public.tableau.com/app/profile/prima.sukrono/viz/MikrotransJakarta/MikrotransJakarta?publish=yes)**