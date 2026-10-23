# Join the Squad - Pendaftaran Player Valorant ITERA

Tugas Individu 3 - Pengembangan Aplikasi Web
Topik: Tabel, Formulir, Layout, dan Web Media

| | |
|---|---|
| **Nama** | Sena Permatasari |
| **NIM** | 124140018 |
| **Kelas** | [isi kelas] |
| **Program Studi** | Teknik Informatika |
| **Institusi** | Institut Teknologi Sumatera |

## Deskripsi

Website pendaftaran player Valorant ITERA bertema *Join the Squad*. Website terdiri dari dua halaman HTML dan satu file CSS yang dipakai bersama. Form pendaftaran mengirim data dengan method GET, sehingga data terlihat sebagai query string di URL. Halaman detail menampilkan data dummy dalam bentuk tabel.

Tampilan mengambil tema Valorant: warna navy gelap dengan aksen merah, kotak bersudut terpotong, dan ornamen latar (cahaya merah, garis diagonal, bentuk huruf V) yang dibuat murni dengan CSS, tanpa gambar.

## Struktur File

```
.
├── pendaftaran.html   # Halaman form pendaftaran (method GET)
├── detail.html        # Halaman detail player (tabel data dummy)
├── style.css          # Gaya bersama untuk kedua halaman
└── README.md
```

## Cara Menjalankan

1. Simpan ketiga file (`pendaftaran.html`, `detail.html`, `style.css`) dalam satu folder.
2. Buka `pendaftaran.html` di browser.
3. Isi form, lalu klik **Lock In**. Browser akan membuka `detail.html` dengan data pada query string di address bar.

Tidak perlu server atau instalasi apa pun. Font Oswald dan Rajdhani dimuat dari Google Fonts, jadi butuh koneksi internet agar tampil sesuai desain. Tanpa internet, browser memakai font cadangan.

## Fitur

### pendaftaran.html

- Form dengan `action="detail.html"` dan `method="get"`.
- Isian dikelompokkan dengan `<fieldset>` dan `<legend>`: **Data Diri** dan **Data Game**.
- Layout form dua kolom dengan CSS Grid (`.grid-form`), isian lebar penuh memakai `.penuh`.
- Validasi dengan atribut `required` dan `pattern`:
  - NIM: 9 digit angka (`[0-9]{9}`)
  - No. HP: diawali 08 (`08[0-9]{8,11}`)
  - Riot ID: berformat `Nama#TAG`
- Agent Main memakai `<input>` dengan `<datalist>`, jadi bisa dipilih dari daftar atau diketik manual.
- Rank memakai `<select>`, Role Utama memakai radio button.
- `<textarea>` Alasan Bergabung (opsional).
- Tombol **Lock In** (`submit`) dan **Reset** (`reset`) ditata dengan Flexbox.

### detail.html

- Tiga kartu ringkasan (Role, Agent, Rank) ditata dengan Flexbox.
- Tabel data player dengan `<caption>`, `<thead>`, dan `<tbody>`.
- Baris sub-judul memakai `colspan="2"`.
- Data bersifat dummy dan ditulis langsung di HTML. Halaman ini tidak membaca query string.

## Query String

Form mengirim data dalam format:

```
detail.html?key1=value1&key2=value2&...
```

Contoh hasil pengiriman form:

```
detail.html?nama=Sena+Permatasari&nim=124140018&hp=085184467861&email=sena.124140018%40student.itera.ac.id&riotid=Sena%23ITERA&rank=Gold&role=Duelist&agent=Jett&alasan=Ingin+berlatih+bareng
```

| Key | Elemen | Keterangan |
|---|---|---|
| `nama` | text | Spasi diubah menjadi `+` |
| `nim` | text | Divalidasi pattern 9 digit |
| `hp` | tel | Divalidasi pattern, diawali 08 |
| `email` | email | `@` di-encode menjadi `%40` |
| `riotid` | text | `#` di-encode menjadi `%23` |
| `rank` | select | Yang dikirim adalah atribut `value` |
| `role` | radio | Hanya satu nilai yang terkirim |
| `agent` | input + datalist | Bisa dipilih atau diketik |
| `alasan` | textarea | Spasi diubah menjadi `+` |

## Selector CSS yang Digunakan

| Jenis | Contoh |
|---|---|
| Universal | `*` |
| Element | `body`, `table`, `header`, `footer` |
| Class | `.box`, `.btn`, `.kartu`, `.grid-form` |
| Descendant | `.box h2`, `.catatan code`, `nav a` |
| Grouping | `h1, h2` dan `input:focus, select:focus` |
| Attribute | `input[type="radio"]`, `th[colspan].sub` |
| Pseudo-class | `:hover`, `:focus`, `:nth-child(even)`, `:last-child` |
| Pseudo-element | `::placeholder`, `body::before`, `body::after` |

## Responsif

Dengan `@media (max-width: 480px)`, form dua kolom berubah menjadi satu kolom di layar HP.

## Catatan

- Halaman detail memakai data dummy, bukan data dari form.
- Ornamen latar dibuat dengan CSS (`body::before` dan `body::after`), tidak memakai file gambar.