# PLAN.md — Universal 2D Arcade Game Roadmap (Untuk Siswa)

Dokumen ini adalah rencana kerja universal dan log perkembangan proyek pembuatan game arcade 2D dalam 1 file `index.html`. Dokumen ini diperbarui secara otomatis oleh AI setiap kali ada perubahan kode sebelum push ke GitHub.

---

## 1. Ikhtisar Game

- **Judul Game**: Crystal Parkour
- **Genre**: 2D Arcade Platformer (Parkour)
- **Format**: Single-File HTML (`index.html`) tanpa dependensi eksternal
- **Platform**: Web Browser (Desktop & Mobile Responsive)
- **Audio**: Web Audio API Sintetis
- **Penyimpanan**: LocalStorage (`arcade_leaderboard`, `arcade_last_username`, `arcade_character`)
- **Kebijakan Caching**: Zero-Cache (`no-cache, no-store, must-revalidate`)
- **Deployment**: GitHub Pages (Branch `main`, path `/`)
- **URL Live**: https://syakirakhairunnisa23.github.io/crystal-parkour/
- **Karakter**: 3 hewan pilihan dengan statistik dan dunia berbeda — Kucing Oren (seimbang/padang rumput), Kelinci Salju (lompat tinggi/hutan sakura), Rubah Api (lari cepat/senja).
- **Konsep**: Hewan pilihan pemain menjelajahi pulau terapung untuk mengumpulkan kristal. Setelah kristal terkumpul, boss penjaga muncul dan wajib dikalahkan sebelum ke pulau berikutnya. Mekanik: lari, lompat, lompat ganda, hindari duri dan biji pohon yang jatuh dengan peringatan.
- **Status Saat Ini**: Playable end-to-end (menu -> pilih karakter -> 3 pulau + 3 boss -> kemenangan), leaderboard Top 10 aktif, audio sintetis, partikel, layar jeda.

---

## 2. Fase Pengembangan Universal

### Phase 0: Brainstorming & Desain Game
- [x] Siswa menentukan ide & tema game: Crystal Parkour (hewan + pulau terapung + kristal).
- [x] Menentukan kontrol permainan: keyboard (kiri/kanan, A/D, Spasi), klik, dan tombol sentuh.
- [x] Menentukan aturan menang/kalah: kumpulkan semua kristal lalu kalahkan boss; jatuh, duri, biji pohon, atau proyektil boss = kalah.
- [x] Menentukan gaya visual: kartun cerah dengan efek glow neon pada kristal.
- [x] Menentukan variasi karakter hewan (Kucing, Kelinci, Rubah) beserta statistik dan tema latar masing-masing.
- [x] Menentukan desain boss penjaga per pulau (Raja Duri, Golem Kristal, Naga Bayangan) dengan mekanik injak kepala.

### Phase 1: Setup Single-File `index.html`
- [x] Buat kerangka HTML5 dengan meta tag **Zero-Cache**.
- [x] Siapkan kanvas responsif dengan rasio layar tetap 3:2 (480x320).
- [x] Susun struktur kode modular 8 blok di JavaScript.
- [x] Siapkan game loop utama (`requestAnimationFrame`) dengan delta time.

### Phase 2: Username & Leaderboard LocalStorage
- [x] Buat modal input username dengan validasi nama (1-15 karakter, anti-XSS).
- [x] Simpan dan baca username terakhir dari `arcade_last_username`.
- [x] Buat fungsi penyimpanan dan penyortiran Top 10 skor di `arcade_leaderboard`.
- [x] Buat tampilan antarmuka (UI) tabel peringkat skor di menu game.

### Phase 3: Mekanik Inti Permainan (Core Gameplay)
- [x] Sistem status game (`MENU`, `PLAYING`, `PAUSED`, `GAMEOVER`, `LEVELCOMPLETE`, `WIN`).
- [x] Karakter pemain (pergerakan, batas layar, coyote time, lompat ganda).
- [x] Rintangan / musuh (duri statis + biji pohon jatuh dengan posisi acak).
- [x] Deteksi tabrakan (Collision Detection) dan perhitungan skor + bonus waktu.
- [x] Boss fight per pulau: HP bar, lompatan ke arah pemain, proyektil, dan serangan injak kepala.
- [x] Penyesuaian platform dengan jangkauan lompat tiap karakter (gap maksimal 80 px, tanjakan maksimal 80 px; terverifikasi uji otomatis).
- [x] Hujan biji pohon diberi peringatan (marker segitiga + garis putus-putus) sebelum jatuh, dengan jeda dan kecepatan yang meningkat per level.

### Phase 4: Efek Suara & Visual Juice
- [x] Efek suara arcade sintetis dengan Web Audio API (lompat, lompat ganda, kristal, tabrakan, injak boss, level selesai, game over).
- [x] Efek ledakan partikel sederhana saat mengambil kristal, lompat ganda, dan tabrakan.
- [x] Efek getar layar (screen shake) saat tabrakan.
- [x] Efek glow kristal, awan bergerak, dan animasi naik-turun kristal.
- [x] Latar belakang dinamis per karakter: padang rumput berawan (Kucing), hutan sakura berkelopak (Kelinci), senja dengan bara api (Rubah), termasuk warna platform yang serasi.
- [x] Layar pemilihan karakter dengan pratinjau karakter dan statistik.

### Phase 5: Publikasi GitHub Pages
- [x] Inisialisasi git dan branch `main`.
- [x] Buat repository GitHub publik via GitHub CLI (`gh repo create <repo> --public --source=. --remote=origin --push`). *Wajib berstatus Public agar GitHub Pages gratis dapat aktif.*
- [x] Aktifkan GitHub Pages (Metode CLI `gh api` atau manual via Web UI Settings > Pages branch `main` root `/`).
- [x] Kompatibilitas Google AI Studio: Sediakan snippet perintah terminal siap salin jika proyek dilanjutkan lewat antarmuka web.
- [x] Pantau status workflow build di tab Actions (`gh run list`).
- [x] Tes live demo (`https://syakirakhairunnisa23.github.io/crystal-parkour/`) dan pastikan pembaruan langsung tampil tanpa hambatan cache (Zero-Cache test).

---

## 3. Matriks Tugas & Status Pelaksanaan

| ID | Tugas / Fitur | Fase | Status | Pelaksana | Catatan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **T-00** | Pembuatan template `AGENTS.md` & `PLAN.md` untuk Siswa | Fondasi | `DONE` | AI | Template standar single model siap |
| **T-01** | Brainstorming Ide & Konsep Game Spesifik | Phase 0 | `DONE` | Siswa | Crystal Parkour: hewan, pulau terapung, kristal, boss |
| **T-02** | Pembuatan Skeleton `index.html` & Meta Zero-Cache | Phase 1 | `DONE` | AI | 8 blok modular, kanvas 480x320 responsif |
| **T-03** | Modul Input Username & Leaderboard Top 10 | Phase 2 | `DONE` | AI | LocalStorage CRUD, validasi 1-15 karakter, anti-XSS |
| **T-04** | Logika Pergerakan, Rintangan & Tabrakan | Phase 3 | `DONE` | AI | 3 pulau, lompat ganda, duri, biji jatuh, bonus waktu |
| **T-05** | Efek Suara Synth Web Audio API & Partikel | Phase 4 | `DONE` | AI | Audio sintetis, partikel, screen shake, pause |
| **T-06** | Deployment GitHub Pages via GitHub CLI (`gh`) | Phase 5 | `DONE` | AI | Live di https://syakirakhairunnisa23.github.io/crystal-parkour/ (build sukses) |
| **T-07** | Pemilihan 3 Karakter Hewan + Tema Latar Berbeda | Phase 4 | `DONE` | AI | Kucing, Kelinci, Rubah; statistik & `arcade_character` tersimpan |
| **T-08** | Boss Fight Sebelum Pulau Berikutnya | Phase 3 | `DONE` | AI | 3 boss, HP bar, proyektil, injak kepala, retry khusus boss |
| **T-09** | Penyesuaian Platform & Hujan Rintangan | Phase 3 | `DONE` | AI | Gap/tinggi teruji; hazard diberi warning marker & skala per level |

*Status: `TODO` | `IN-PROGRESS` | `DONE`*

---

## 4. Changelog & Riwayat Revisi

| Versi | Tanggal | Pelaksana | Ringkasan Perubahan | Referensi Commit |
| :--- | :--- | :--- | :--- | :--- |
| **v0.4.1** | 2026-11-07 | AI | Perbaikan encoding `PLAN.md` ke UTF-8 dan penambahan `.nojekyll` agar build GitHub Pages tidak lagi diproses Jekyll; deploy diverifikasi cocok dengan file lokal | `c605073` |
| **v0.4.0** | 2026-11-07 | AI | Menambahkan 3 karakter hewan pilihan (Kucing/Kelinci/Rubah) dengan statistik & tema latar berbeda, layar pemilihan karakter berpratinjau, boss penjaga di akhir setiap pulau (HP bar, lompatan, proyektil, injak kepala, retry boss), penataan ulang platform sesuai jangkauan lompat, serta peringatan visual sebelum biji pohon jatuh dengan kesulitan bertingkat | `e002f26` |
| **v0.3.1** | 2026-10-31 | AI | Publikasi repository publik `crystal-parkour`, aktivasi GitHub Pages dari branch `main` root `/`, build sukses, dan verifikasi live site (status `built`, halaman memuat game) | `48c2a51` |
| **v0.3.0** | 2026-10-31 | AI | Perbaikan total `index.html`: struktur duplikat yang menyebabkan `SyntaxError` dibersihkan, input lompat keyboard (Spasi/atas/W) diperbaiki, lompat ganda + coyote time, layar jeda (P/Esc), partikel & screen shake, HUD/kanvas responsif, tombol sentuh berbasis pointer, skor disimpan saat game over & kemenangan tanpa duplikasi run, serta sanitasi leaderboard lebih ketat | `9493795` |
| **v0.2.2** | 2026-10-24 | AI | Menambahkan panduan alur integrasi khusus Google AI Studio & penegasan repo wajib Public | `07475fb` |
| **v0.2.1** | 2026-10-24 | AI | Menambahkan panduan detail aktivasi GitHub Pages (CLI gh api & Web UI visual) serta troubleshooting | `3aaf671` |
| **v0.2.0** | 2026-10-24 | AI | Konfigurasi ulang ke Single Model AI untuk siswa, modularisasi 8 blok kode, dan penyesuaian matriks tugas | `2954bb0` |
| **v0.1.0** | 2026-10-24 | AI | Inisialisasi awal file sistem `AGENTS.md` dan universal blueprint `PLAN.md` | `47aa88e` |
