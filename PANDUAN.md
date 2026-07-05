# Panduan Setup — Sistem Scan, Print & Collect (PKSP 2026)

## 1. Firebase config
Buka `index.html`, cari `firebaseConfig` dan gantikan `GANTIKAN_API_KEY`, `messagingSenderId` dan `appId` dengan nilai sebenar dari projek **qestion-conference-talk** (Firebase Console → Project settings → General → Your apps).

## 2. Firestore rules
Tambah rules ini untuk koleksi baharu (kekalkan rules Q&A sedia ada):

```
match /peserta_pksp2026/{docId} {
  allow read: if true;
  allow create, update: if true;
  allow delete: if false;
}
```

> Nota: rules terbuka sesuai untuk tempoh persidangan sahaja. Selepas event, tukar `allow create, update: if false;` untuk kunci data.

## 3. Deploy ke GitHub Pages
1. Buat repo baharu contohnya `Daftar` dalam organisasi `pkspconference2026`.
2. Upload `index.html` dan `tiket.html`.
3. Settings → Pages → deploy dari branch `main`.
4. URL kaunter: `https://pkspconference2026.github.io/Daftar/`
5. URL tiket peserta: `https://pkspconference2026.github.io/Daftar/tiket.html?kod=PKSP26-XXXXXX`

## 4. Aliran kerja sebelum persidangan
1. Sediakan CSV peserta: `nama,jawatan,organisasi,negeri,kategori,telefon,emel`
   - kategori: `peserta`, `vip`, `penceramah`, `urusetia`, `penaja`, `media`
2. Tab **Senarai & Statistik** → **Import CSV**. Kod QR unik (cth `PKSP26-A1B2C3`) dijana automatik.
3. **Eksport CSV** untuk dapatkan kod setiap peserta.
4. Hantar pautan tiket melalui e-mel/WhatsApp:
   `.../tiket.html?kod=PKSP26-A1B2C3`
   Untuk WhatsApp pukal, gunakan mail merge atau format:
   `https://wa.me/60123456789?text=Tiket%20PKSP%202026%20anda:%20https://...tiket.html?kod=PKSP26-A1B2C3`

## 5. Pada hari persidangan
- **Lorong A**: petugas buka tab QR Express di telefon/tablet → Mula Scan → scan → cetak tag.
- **Lorong B**: cari ikut nama/telefon/emel → Daftar Masuk → cetak.
- **Lorong C**: isi borang walk-in → automatik direkod hadir → cetak.

## 6. Cetakan tag
- Saiz tag: **A6 (105mm × 148mm)** — sesuai dengan holder lanyard standard.
- Sambungkan pencetak (cth. pencetak label thermal atau laser dengan kertas A6) ke tablet/laptop kaunter.
- Dalam dialog cetak, pastikan saiz kertas A6 dan margin `None`.
- Jalur warna bawah tag mengikut kategori: Hijau (Peserta), Emas (VIP), Biru (Penceramah), Merah (Urus Setia), Ungu (Penaja/Media).
