# Portal Layanan Akademik

ILK264330 Pemrograman Berbasis Platform – Tugas Pertemuan 5: Responsive & Accessible Web Client
Nur Alam · 202451039 · S1 Ilmu Komputer, Universitas Pattimura

Halaman web untuk mengajukan layanan akademik secara online (Surat Aktif Kuliah, Transkrip Sementara, Cuti Akademik, dan Legalisir). Dibuat dengan HTML dan CSS, tanpa JavaScript.

## Keputusan desain

- **Batas perubahan tampilan (breakpoint) dipilih berdasarkan isi halaman, bukan jenis perangkat.** Sekitar 600 px kartu dan form jadi 2 kolom, sekitar 900 px bagian atas dibagi dua, dan sekitar 1100 px keempat kartu muat dalam satu baris.
- **Link di kartu memakai `<a>`**, karena fungsinya hanya pindah ke bagian form. **"Kirim permohonan" memakai `<button>`**, karena fungsinya mengirim data.
- **Jenis layanan memakai radio, bukan dropdown**, karena pilihannya cuma 4 dan semuanya langsung terlihat.
- **Alur permohonan memakai daftar bernomor (`<ol>`)**, karena isinya langkah yang berurutan.
- **Pesan salah berupa tulisan dan ikon ⚠, bukan hanya warna merah**, supaya tetap jelas bagi orang yang buta warna. Pesan baru muncul setelah pengguna salah mengisi.
- **Form memakai `method="get"`**, karena belum ada server. Data yang dikirim terlihat di URL dan di tab Network.
- **Semester tidak wajib diisi**, karena layanan Legalisir juga untuk alumni.
- **Logo memakai `alt=""` (kosong)**, karena nama universitas sudah tertulis di sebelahnya. Kalau diisi, pembaca layar akan membacanya dua kali.
- **Warna dipilih supaya tulisan mudah dibaca.** Kontras tulisan dan latar dicek di DevTools dan semuanya di atas batas minimal 4.5:1.

## Hasil pengujian

| Pengujian | Hasil | Bukti |
|---|---|---|
| Layar HP 360 px | Semua 1 kolom, tidak ada scroll ke samping | `evidence/tampilan-360px.png` |
| Layar tablet 768 px | Kartu 2 kolom, form tetap nyaman dibaca | `evidence/tampilan-768px.png` |
| Layar laptop 1280 px | Kartu 4 kolom, tulisan tidak terlalu melebar | `evidence/tampilan-1280px.png` |
| Elements & Styles | `.footer-grid` memakai `display: grid` | `evidence/devtools-elements.png` |
| Network (reload) | Semua file berhasil dimuat, status 200 | `evidence/devtools-network.png` |
| Network (nama CSS salah) | `style.css` tidak ditemukan, status 404 | `evidence/devtools-network-404.png` |
| Accessibility | Isian nama dikenali sebagai kotak teks "Nama lengkap" dan wajib diisi | `evidence/devtools-accessibility.png` |

## Catatan debugging

1. **Judul tertutup menu saat klik link di menu.** Diperbaiki dengan `scroll-padding-top: 6rem`.
2. **Menu terlalu lebar di layar 360 px.** Diperbaiki dengan `flex-wrap: wrap`, jadi menu turun ke baris berikutnya.
3. **Kotak form (fieldset) bisa melebar keluar layar** karena pengaturan bawaan browser. Diperbaiki dengan `min-width: 0`.
4. **Link di kartu tidak sejajar** karena panjang penjelasan berbeda. Diperbaiki dengan `margin-top: auto`.
5. **Isian salah hanya ditandai warna merah.** Diperbaiki dengan menambah tulisan dan ikon ⚠.
6. **Uji file tidak ditemukan (404).** Nama `styles.css` diganti jadi `style.css`, lalu halaman di-reload. Tab Network menunjukkan status 404 dan halaman tampil polos. Setelah namanya dikembalikan, status kembali 200.