# Tata Surya Berita Kabupaten Bandung

## Pasang
1. Buat repositori GitHub, unggah semua isi folder ini (termasuk folder .github).
2. Settings > Secrets and variables > Actions, tambahkan secret:
   - `ANTHROPIC_API_KEY` (wajib) dari console.anthropic.com
   - `YOUTUBE_API_KEY` (opsional, gratis) dari Google Cloud Console: aktifkan "YouTube Data API v3", buat API key
   - `X_BEARER_TOKEN` (opsional, X API berbayar)
3. Settings > Pages > Source: branch `main`, folder `/ (root)`.
4. Tab Actions > "Perbarui data berita" > Run workflow. Sesudahnya berjalan otomatis tiap jam.

## Catatan
- Sentimen dinilai dari judul + kutipan isi artikel (kalau isi berhasil diambil), lalu disimpan di `cache.json` agar berita yang sama tidak dinilai ulang.
- Media sosial diperbarui tiap 4 jam (ubah lewat env `SOCIAL_EVERY_HOURS`) agar kuota YouTube (10.000 unit/hari) cukup.
- Instagram, TikTok, dan Facebook tidak punya pencarian publik yang bisa dipakai bebas, jadi belum disertakan.
- Uji lokal: `pip install -r requirements.txt && ANTHROPIC_API_KEY=... python collector.py`
