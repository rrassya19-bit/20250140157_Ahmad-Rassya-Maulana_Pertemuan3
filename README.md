# Asisten AI Untuk UMKM

Halaman web statis ini memuat header informasi, menu navigasi, kartu profil mahasiswa, formulir input data pengguna, galeri logo, serta footer. Proyek ini disusun sebagai pemenuhan tugas Praktikum Pertemuan 3 pada mata kuliah TI-501 Pengembangan Aplikasi Web dengan fokus pembelajaran mengenai CSS3 Layout Responsif.

## Identitas
- **Nama:** Ahmad Rassya Maulana
- **NIM:** 20250140157
- **Mata Kuliah:** TI-501 Pengembangan Aplikasi Web
- **Pertemuan:** 3 (CSS3 Layout Responsif)

## Tujuan Praktikum
Tujuan praktikum ini adalah merancang antarmuka web modern menggunakan CSS3 dengan menerapkan pemahaman box model, custom properties, Flexbox, CSS Grid, fluid sizing, dan media query berpendekatan mobile-first. Target utamanya adalah menghasilkan tata letak halaman yang rapi, adaptif, dan aksesibel tanpa scroll horizontal baik pada layar smartphone, tablet, maupun desktop.

## Struktur Folder
```text
20250140157_Ahmad-Rassya-Maulana_Pertemuan3/
├── Screenshots/
│   ├── Screenshot 2026-10-01 152321.png
│   └── Screenshot 2026-10-01 152647.png
├── docs/
│   └── Dokumentasi_Asisten_AI_UMKM_Pertemuan3.pdf
├── index.html
├── README.md
└── style.css
```

**Penjelasan berkas dan direktori:**
- `index.html`: Berkas HTML utama yang memuat struktur dokumen semantik dari header hingga footer.
- `style.css`: Berkas stylesheet CSS3 yang mengatur seluruh tata letak, warna, tipografi, grid/flexbox, dan responsivitas.
- `README.md`: Berkas dokumentasi lengkap mengenai penjelasan kode, arsitektur tata letak, dan pemetaan materi praktikum.
- `Screenshots/`: Direktori penyimpan tangkapan layar tampilan antarmuka web pada berbagai ukuran resolusi.
- `docs/`: Direktori penyimpan berkas dokumen PDF laporan dokumentasi praktikum.

## Tampilan Website

Berikut adalah dokumentasi tangkapan layar hasil implementasi halaman web:

![Tampilan Antarmuka 1](Screenshots/Screenshot%202026-10-01%20152321.png)
*Gambar 1: Tampilan antarmuka halaman web (kondisi tampilan 1).*

![Tampilan Antarmuka 2](Screenshots/Screenshot%202026-10-01%20152647.png)
*Gambar 2: Tampilan antarmuka halaman web (kondisi tampilan 2).*

### Perbandingan Tampilan Desktop dan Mobile
Pada resolusi mobile (layar sempit di bawah 768px), elemen `main` dirender dalam format 1 kolom vertikal bertumpuk agar konten mudah dibaca tanpa ada luapan horizontal. Menu navigasi dapat melakukan *wrap* secara fleksibel. Ketika ukuran layar membesar ke ukuran tablet dan laptop (breakpoint `>= 768px`), layout `main` bertransformasi menjadi CSS Grid 2 kolom dengan kartu profil membentang penuh di baris pertama (`grid-column: 1 / -1`), sementara kartu formulir dan kartu gambar berdampingan secara seimbang di kolom kiri dan kanan.

## Penjelasan Kode HTML (index.html)

### 1. Deklarasi Dokumen & Meta Tag
Bagian `<head>` mendefinisikan standar dokumen HTML5, pengaturan karakter UTF-8, judul halaman, serta meta viewport yang mengontrol skala dan lebar tampilan agar halaman dapat disajikan secara responsif di perangkat bergerak. Tautan CSS dihubungkan melalui tag `<link>`.
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Praktikum 1</title>
    <link rel="stylesheet" href="style.css">
</head>
```

### 2. Header & Navigasi
Elemen semantik `<header>` digunakan untuk memuat identitas utama situs web, sedangkan `<nav>` membungkus tautan navigasi internal yang terhubung ke ID bagian dokumen.
```html
    <header>
        <h1>Asisten AI Untuk UMKM</h1>
        <p>Selamat datang di halaman asisten AI untuk UMKM</p>
    </header>
    
    <nav>
        <a href="#profile">Profile</a> | 
        <a href="#formdata">Form</a>
    </nav>
```

### 3. Bagian Konten Utama (`<main>`)
Elemen `<main>` memuat tiga buah elemen `<section>` sebagai struktur kartu konten:
- **Bagian Profil:** Menggunakan `id="profile"` yang memuat judul nama dan nomor induk mahasiswa.
```html
        <section id="profile">
            <h2>Ahmad Rassya Maulana</h2>
            <p>20250140157</p>
        </section> 
```
- **Bagian Formulir:** Formulir dengan `id="formdata"` memuat input teks nama dengan atribut `required`, pengelompokan pilihan jenis kelamin menggunakan `<fieldset>` dan `<legend>`, serta tombol submit. Pemakaian elemen `<label>` yang dipasangkan dengan atribut `for` dan `id` memastikan aksesibilitas pembaca layar (*screen reader*).
```html
        <section>
            <form id="formdata" action="#">
                <label for="name">Masukkan nama anda:</label><br>
                <input type="text" id="name" name="name" required><br><br>
                
                <fieldset>
                    <legend>Jenis Kelamin:</legend>
                    <input type="radio" name="jenis-kelamin" id="laki-laki" required>
                    <label for="laki-laki">Laki-laki</label><br>
                    <input type="radio" name="jenis-kelamin" id="perempuan">
                    <label for="perempuan">Perempuan</label>
                </fieldset><br>

                <input type="submit" value="Submit">
            </form>
        </section>
```
- **Bagian Gambar:** Menampilkan dua elemen `<img>` yang dilengkapi atribut `alt` deskriptif untuk mendukung aksesibilitas informasi gambar.
```html
        <section>
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRRYqxevuHys9QU-F_OfIi4Co2a_zqFtDzCT8BzQK2-eTz6dSn2E0pYBWQF&s=10" alt="Logo UMKM Komunitas Indonesia">
            <img src="logo-umkm-ai.png" alt="Logo Asisten AI Untuk UMKM berbentuk ikon robot">
        </section>
```

### 4. Footer
Elemen `<footer>` diletakkan di akhir dokumen untuk menutup halaman secara semantik.
```html
    <footer>
        <p>Asisten AI Untuk UMKM</p>
    </footer>
```

## Penjelasan Kode CSS (style.css)

### 1. Custom Properties & Box-Sizing Reset
Menginisialisasi palet warna, radius, dan bayangan pada pseudo-class `:root` untuk konsistensi nilai. Aturan `* { box-sizing: border-box; }` diterapkan agar kalkulasi ukuran elemen mencakup padding dan border secara proporsional.
```css
:root {
  --primary: #173b66;
  --accent: #f28c28;
  --bg-body: #f4f6f9;
  --bg-card: #ffffff;
  --text-main: #1f2937;
  --text-muted: #4b5563;
  --border-color: #e2e8f0;
  --radius-card: 20px;
  --radius-sm: 8px;
  --shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
```

### 2. Gaya Dasar Body
Menentukan tata letak dasar berbasis flex kolom terpusat, warna latar netral, dan font sans-serif bawaan sistem dengan line-height 1.6.
```css
body {
  font-family: sans-serif;
  background-color: var(--bg-body);
  color: var(--text-main);
  line-height: 1.6;
  padding: 1rem 1rem 2rem 1rem;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

### 3. Header & Navigasi
Header menggunakan background warna utama `--primary` dengan tipografi fluid `clamp()`. Navigasi ditata horizontal menggunakan Flexbox dengan kemampuan `flex-wrap: wrap` dan indikator fokus yang jelas.
```css
header {
  width: 100%;
  max-width: 960px;
  background-color: var(--primary);
  color: #ffffff;
  padding: 1.5rem;
  border-radius: var(--radius-card);
  text-align: center;
  box-shadow: var(--shadow);
  margin-bottom: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

header h1 {
  font-size: clamp(1.4rem, 4vw, 2rem);
}

header p {
  font-size: clamp(0.9rem, 2vw, 1rem);
}

nav {
  width: 100%;
  max-width: 960px;
  background-color: var(--bg-card);
  padding: 0.75rem 1.5rem;
  border-radius: var(--radius-card);
  box-shadow: var(--shadow);
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-bottom: 1.25rem;
  color: var(--text-muted);
}

nav a {
  color: var(--primary);
  text-decoration: none;
  font-weight: 600;
  padding: 0.4rem 0.6rem;
  border-radius: var(--radius-sm);
}

nav a:focus {
  outline: 2px solid var(--accent);
}
```

### 4. Layout Konten & Gaya Kartu
Elemen `main` menerapkan CSS Grid dengan nilai dasar 1 kolom `minmax(0, 1fr)`. Setiap kartu `section` diberi latar belakang putih, radius 20px, bayangan halus, dan border pembatas.
```css
main {
  width: 100%;
  max-width: 960px;
  display: grid;
  grid-template-columns: minmax(0, 1fr);
  gap: 1.25rem;
  margin-bottom: 1.5rem;
  align-items: start;
}

main > section {
  background-color: var(--bg-card);
  padding: 1.5rem;
  border-radius: var(--radius-card);
  box-shadow: var(--shadow);
  border: 1px solid var(--border-color);
}
```

### 5. Komponen Formulir & Radio Button
Formulir ditata dengan Flexbox vertikal berjarak seragam (`gap: 0.75rem`), menonaktifkan tag `<br>`, serta menyejajarkan radio button dan labelnya secara horizontal pada satu baris.
```css
#formdata {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

form br {
  display: none;
}

#formdata label {
  font-weight: 500;
  font-size: 0.95rem;
}

#formdata input[type="text"] {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid var(--border-color);
  border-radius: var(--radius-sm);
  font-size: 1rem;
  font-family: inherit;
}

#formdata input[type="text"]:focus {
  outline: 2px solid var(--primary);
  border-color: var(--primary);
}

fieldset {
  border: 1px solid var(--border-color);
  border-radius: var(--radius-sm);
  padding: 0.75rem 1rem;
}

legend {
  padding: 0 0.4rem;
  font-weight: 600;
  color: var(--primary);
  margin-bottom: 0.5rem;
}

fieldset br {
  display: none;
}

input[type="radio"] {
  width: 1.25rem;
  height: 1.25rem;
  margin: 0 0.4rem 0 0;
  padding: 0;
  vertical-align: middle;
  cursor: pointer;
}

fieldset label {
  display: inline-block;
  vertical-align: middle;
  cursor: pointer;
  padding: 0.4rem 0.6rem 0.4rem 0;
  margin-right: 1.25rem;
  font-size: 0.95rem;
}

input[type="submit"] {
  background-color: var(--accent);
  color: #ffffff;
  border: none;
  border-radius: var(--radius-sm);
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  font-weight: 600;
  font-family: inherit;
  cursor: pointer;
  width: 100%;
  min-height: 44px;
}

input[type="submit"]:focus {
  outline: 2px solid var(--primary);
}
```

### 6. Pengaturan Gambar & Footer
Gambar diatur agar tidak melebihi lebar kontainer (`max-width: 100%`) dan mempertahankan rasio aspek (`height: auto`). Footer diberi padding dan pembatas atas yang rapi.
```css
main > section:nth-of-type(3) {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

img {
  max-width: 100%;
  height: auto;
  border-radius: var(--radius-sm);
  display: block;
}

footer {
  width: 100%;
  max-width: 960px;
  text-align: center;
  padding: 1.5rem 1rem;
  color: var(--text-muted);
  font-size: 0.875rem;
  border-top: 1px solid var(--border-color);
  margin-top: auto;
}
```

### 7. Media Query (Mobile-First)
Penerapan breakpoint berjenjang untuk layar tablet (`min-width: 768px`) dan laptop (`min-width: 1024px`).
```css
@media (min-width: 768px) {
  body {
    padding: 1.5rem 1.5rem 2.5rem 1.5rem;
  }

  main {
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1.5rem;
  }

  #profile {
    grid-column: 1 / -1;
  }

  input[type="submit"] {
    width: auto;
    align-self: flex-start;
  }
}

@media (min-width: 1024px) {
  body {
    padding: 2rem 1.5rem 3rem 1.5rem;
  }
}
```

### Tabel Ringkasan Teknik Layout
| Elemen | Teknik Layout | Alasan Penggunaan |
| :--- | :--- | :--- |
| `body` | Flexbox (`column`, `align-items: center`) | Menjaga seluruh kontainer terpusat di tengah layar secara horizontal |
| `header` | Flexbox (`column`, `gap: 0.5rem`) | Mengatur susunan judul dan paragraf deskripsi terpusat |
| `nav` | Flexbox (`row`, `flex-wrap: wrap`) | Menjaga tautan navigasi tersusun horizontal dan adaptif turun baris saat layar sempit |
| `main` | CSS Grid (`repeat`, `minmax(0, 1fr)`) | Mengontrol sistem tata letak 2 dimensi (1 kolom di mobile, 2 kolom di tablet/desktop) |
| `#profile` | Flexbox (`column`, `grid-column: 1 / -1`) | Menampilkan data profil vertikal dan membentang penuh di atas grid |
| `#formdata` | Flexbox (`column`, `gap: 0.75rem`) | Memberikan jarak vertikal yang rapi dan konsisten antar-input |
| `section (gambar)` | Flexbox (`column`, `align-items: center`) | Menyelaraskan susunan logo di tengah area kartu |

## Penerapan Materi Pertemuan 3

| Konsep Materi | Bagian Kode / Selector Terkait | Keterangan Implementasi |
| :--- | :--- | :--- |
| **Box Model** | `* { box-sizing: border-box; }`, `main > section` | Penentuan padding, margin, border, dan border-radius tanpa memicu overflow |
| **Custom Properties** | `:root`, `var(--primary)`, `var(--accent)`, dll. | Deklarasi variabel terpusat untuk palet warna, radius, dan shadow |
| **Selector & Cascade** | `input[type="text"]`, `main > section:nth-of-type(3)` | Penggunaan selector spesifik dan selector turunan yang bersih tanpa class tambahan |
| **Flexbox** | `header`, `nav`, `#formdata`, `section:nth-of-type(3)` | Pengaturan layout 1 dimensi dengan properti `gap`, `justify-content`, dan `flex-wrap` |
| **CSS Grid** | `main`, `@media (min-width: 768px) { main }` | Penataan layout 2 dimensi dengan `minmax(0, 1fr)`, `gap`, dan `grid-column: 1 / -1` |
| **Media Query** | `@media (min-width: 768px)`, `@media (min-width: 1024px)` | Pendekatan mobile-first untuk adaptasi ukuran layar bertahap |
| **Fluid Layout** | `clamp()`, `max-width: 960px`, `width: 100%` | Penggunaan ukuran adaptif agar tipografi dan kontainer elastis |
| **Aksesibilitas** | `:focus`, `input[type="radio"] + label`, `alt` | Outline fokus kontras, target sentuh minimal 44px, dan keterkaitan label formulir |

## Aspek Responsif dan Aksesibilitas

1. **Adaptasi Layar (Mobile-First):**
   - **Layar Smartphone (360px - 767px):** Tata letak 1 kolom linier, teks navigasi dapat melakukan pembungkusan (*wrap*), tombol submit membentang penuh (*width: 100%*), dan tidak ada scrollbar horizontal.
   - **Layar Tablet (768px - 1023px):** Konten utama bertransformasi menjadi 2 kolom grid. Tombol submit menyesuaikan ukuran teksnya secara natural.
   - **Layar Desktop (>= 1024px):** Pembatasan lebar maksimal kontainer pada `960px` dengan posisi horizontal terpusat (*center-aligned*) dan padding ruang luar yang lebih lapang.
2. **Aksesibilitas (A11y):**
   - Setiap elemen formulir dihubungkan secara semantik dengan `<label for="...">`.
   - Tombol submit dan input memiliki tinggi sentuh nyaman (minimal 44px) yang ramah layar sentuh (*touch friendly*).
   - Indikator status `:focus` terlihat tegas dengan garis outline tebal (`2px solid`) untuk navigasi keyboard.
   - Kontras warna antara teks gelap dan latar belakang terang memenuhi standar kenyamanan membaca.
