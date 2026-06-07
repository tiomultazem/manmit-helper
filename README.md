# ManMit Helper

Aplikasi otomasi berbasis Python untuk melakukan ekstraksi dan *unmasking* data Mitra BPS secara massal dari portal **Manajemen Mitra BPS** (https://manajemen-mitra.bps.go.id).

---

## 🚀 Fitur Utama

- **Login SSO**
- **Fetch Data Lengkap Mitra** 
- **Captcha? HAHAHAHAHAHAHA (evil laugh)**

---

## 📂 Struktur Proyek

Berikut adalah berkas penting di dalam repositori ini:

| Nama Berkas / Folder | Deskripsi |
| :--- | :--- |
| `app.py` | Berkas utama, aplikasi jalan via CLI |
| `session.json` *(Auto-generated)* | Menyimpan sesi. |
| `mitra_details_cache.json` *(Auto-generated)* | Basis data lokal hasil fetch. |
| `env` | Menyimpan kredensial akun BPS pengguna (`USER` dan `PASS`). Rename dengan menambahkan titik di depan agar bisa dipakai. |

---

## 🛠️ Prasyarat Sistem

Pastikan perangkat Anda sudah terpasang komponen berikut:
1. **Python 3.12+** (Sangat disarankan menggunakan distribusi Anaconda/Miniconda).
2. Pustaka Python pendukung:
   - `requests`
   - `beautifulsoup4`
   - `opencv-python` (OpenCV)
   - `numpy`
   - `pillow`
   - `python-dotenv`

Instalasi dependensi dapat dilakukan dengan menjalankan perintah:
```bash
pip install requests beautifulsoup4 opencv-python numpy pillow python-dotenv
```

---

## ⚙️ Panduan Konfigurasi

Sebelum menjalankan program:

**Edit berkas `env`** di direktori utama proyek dengan mengisi dengan kredensial BPS Anda:
   ```env
   USER=username_nip_anda
   PASS=password_anda
   ```
kemudian ganti namanya menjadi `.env`

---

## 📖 Cara Penggunaan

Jalankan skrip utama `app.py` menggunakan Python:
```bash
python app.py
```

Setelah aplikasi berjalan, Anda akan disambut dengan menu CLI interaktif:

```text
=============================================
         BPS MITRA AUTOMATION SYSTEM
=============================================
1. Status Login
2. Login
3. Get Mitra
4. Download to CSV
5. Keluar
=============================================
Pilih menu (1-5):
```

### Penjelasan Menu:
1. **Status Login:** Memeriksa apakah sesi login saat ini (dari `session.json`) masih aktif dan valid di server BPS. Menampilkan nama pengguna dan wilayah kerja jika berhasil terhubung.
2. **Login:** Melakukan otentikasi ulang ke Keycloak SSO BPS dan memperbarui token/cookies jika sesi sebelumnya kedaluwarsa.
3. **Get Mitra:** Memulai penarikan data Mitra BPS berdasarkan tahun target (default: 2026). Sistem akan mendeteksi wilayah kerja dari token Anda, mengunduh daftar mitra, lalu mulai meng-unmask NIK/NPWP/Rekening.
4. **Download to CSV:** Mengekspor data Mitra BPS yang telah terkumpul dan di-unmask ke dalam format file `.csv`. Anda akan diminta memilih lokasi penyimpanan melalui dialog penyimpanan sistem.
5. **Keluar:** Menghentikan program dengan aman.

---

## 🧩 Captcha?? HAHAHAHAHAHAHA

Aplikasi ini akan menerabas captcha. How? Magic, bruh. Magic.

---

## ⚠️ Catatan Keamanan & Batasan
- Gunakan aplikasi ini secara bijak dan patuhi kebijakan penggunaan data di lingkungan Badan Pusat Statistik.
- Pastikan berkas `.env`, `session.json`, dan `mitra_details_cache.json` **tidak diunggah** ke repositori publik untuk melindungi kerahasiaan kredensial dan data pribadi Mitra BPS yang berhasil diunduh.

---

## ⚖️ Lisensi & Hak Cipta / License & Copyright

**Copyright © 2026 Gilang Wahyu Prasetyo, BPS Kabupaten Tabalong.**

### Bahasa Indonesia (Indonesian)
Perangkat lunak ini menggunakan lisensi **Hanya Untuk Penggunaan Internal (Internal Use Only)**:
- Hanya boleh digunakan untuk kebutuhan internal Badan Pusat Statistik (BPS) Kabupaten Tabalong.
- Dilarang mendistribusikan ulang, memodifikasi, atau menggunakan perangkat lunak ini untuk tujuan di luar kepentingan operasional resmi yang telah ditentukan tanpa izin tertulis.

### English
This software is licensed under the **Internal Use Only** terms:
- Permitted solely for internal use within BPS Kabupaten Tabalong.
- Redistribution, modification, or any other use of this software outside official operational purposes without prior written consent is strictly prohibited.
