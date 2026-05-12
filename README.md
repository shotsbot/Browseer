# 🌐 ChromeBrowser — Android Browser App
### Tampilan & Fitur Mirip Google Chrome
#### Dibangun menggunakan AIDE / Code on the Go di Android

---

## 📁 Struktur Proyek

```
ChromeBrowser/
├── build.gradle                          ← Project build config
├── settings.gradle                       ← Project settings
└── app/
    ├── build.gradle                      ← App dependencies & SDK
    └── src/main/
        ├── AndroidManifest.xml           ← Permissions & activity config
        ├── java/com/chromebrowser/app/
        │   ├── MainActivity.java         ← 🧠 Browser utama (600+ baris)
        │   ├── BrowserTab.java           ← Model untuk setiap tab
        │   └── DataManager.java         ← Bookmarks, history, settings
        └── res/
            ├── layout/
            │   ├── activity_main.xml     ← Layout UI utama
            │   ├── item_tab.xml          ← Layout setiap tab di tab strip
            │   └── item_browser_entry.xml ← Layout item bookmark/history
            ├── drawable/
            │   ├── bg_url_bar.xml        ← Background URL bar (rounded)
            │   ├── bg_tab_active.xml     ← Tab aktif style
            │   ├── bg_tab_inactive.xml   ← Tab tidak aktif style
            │   ├── bg_home_search.xml    ← Search bar di New Tab Page
            │   └── bg_favicon_circle.xml ← Circular favicon background
            ├── values/
            │   ├── colors.xml            ← Palet warna Chrome
            │   ├── strings.xml           ← Semua teks/string
            │   └── styles.xml            ← Theme & widget styles
            └── xml/
                └── file_paths.xml        ← FileProvider paths
```

---

## ✨ Fitur yang Tersedia

| Fitur | Keterangan |
|-------|------------|
| 🗂️ Multi-Tab | Buka banyak tab, switch & close tab |
| 🔒 Tab Incognito | Mode privat, tidak menyimpan history/cookie |
| 🏠 New Tab Page | Logo Google + shortcut 8 situs populer |
| 🔍 URL / Search Bar | Auto-detect URL atau query pencarian |
| ← → Navigasi | Tombol Back, Forward, Reload, Stop |
| 📑 Bookmark | Tambah/hapus/lihat bookmark |
| 🕐 History | Lihat & hapus history browsing |
| 🔎 Find in Page | Cari teks dalam halaman web |
| 💻 Desktop Mode | Toggle user-agent desktop/mobile |
| ⬇️ Download | Otomatis download file via DownloadManager |
| 📤 Share | Share URL halaman ke aplikasi lain |
| ℹ️ Page Info | Lihat info URL + status HTTPS |
| ⚙️ Settings | Ganti search engine, JS on/off, clear cache |
| 📎 File Upload | Support input type=file di web form |
| 🌍 External Links | Buka link eksternal (tel:, mailto:, dll) |
| 🔐 SSL Warning | Alert jika sertifikat bermasalah |
| 📍 Geolocation | Support izin lokasi untuk website |

---

## 🛠️ Cara Build di AIDE

### Langkah 1 — Install AIDE
1. Download **AIDE (Android IDE)** dari Play Store
2. Buka AIDE → beri izin akses storage

### Langkah 2 — Buat Project
1. Di AIDE: **New → Android App**
2. Nama: `ChromeBrowser`
3. Package: `com.chromebrowser.app`
4. Min SDK: `21`

### Langkah 3 — Salin Semua File
Salin semua file ke lokasi yang sesuai di project AIDE kamu:
- File `.java` → ke folder `src/main/java/com/chromebrowser/app/`
- File `layout/*.xml` → ke `res/layout/`
- File `drawable/*.xml` → ke `res/drawable/`
- File `values/*.xml` → ke `res/values/`
- File `xml/*.xml` → ke `res/xml/` (buat folder jika belum ada)
- Replace `AndroidManifest.xml` yang ada

### Langkah 4 — Update build.gradle
Di file `app/build.gradle`, pastikan dependencies ada:
```gradle
dependencies {
    implementation 'androidx.appcompat:appcompat:1.5.1'
    implementation 'com.google.android.material:material:1.7.0'
    implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
    implementation 'androidx.core:core:1.9.0'
    implementation 'androidx.recyclerview:recyclerview:1.2.1'
    implementation 'androidx.cardview:cardview:1.0.0'
    implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.1.0'
}
```

### Langkah 5 — Build & Run
1. AIDE → **Build → Build Project**
2. Tunggu proses Gradle sync & compile
3. Tap **Run** (tombol ▶) untuk install & jalankan

---

## 🚀 Alternatif: Build via Sketchware Pro

Jika menggunakan Sketchware Pro:
1. Import sebagai **Custom Activity** / gunakan WebView component
2. Tambahkan permissions di Manifest
3. Implementasikan logika WebView secara manual via Activity Event

---

## 📱 Screenshot Fitur Utama

```
┌─────────────────────────────────────┐
│  [Tab1] [Tab2 ✕] [Tab3 ✕]  [+]    │  ← Tab Strip
├─────────────────────────────────────┤
│  ◀  ▶  [ 🔒 google.com    ↺ ] [⋮] │  ← Toolbar
├─────────────────────────────────────┤
│▓▓▓▓▓▓▓░░░░░░░░░░░░░░░░░░░░░░░░░░░│  ← Progress Bar
├─────────────────────────────────────┤
│                                     │
│          G  o  o  g  l  e           │  ← New Tab Page
│                                     │
│  [ 🔍  Search Google or type URL ] │
│                                     │
│  [G] [YT] [Wiki] [GH]              │
│  [TW] [RD] [Mail] [Map]             │  ← Quick Access
│                                     │
└─────────────────────────────────────┘
```

---

## ⚠️ Catatan Penting

- **Internet Permission** wajib ada di Manifest
- **usesCleartextTraffic="true"** untuk akses HTTP (non-HTTPS)
- Untuk Android 10+ download otomatis mungkin perlu permission tambahan
- WebView JavaScript enabled by default — bisa dimatikan di Settings

---

## 🔧 Kustomisasi

### Ganti Search Engine Default
Di `DataManager.java`, ubah:
```java
return prefs.getString(KEY_SEARCH_ENGINE, "https://www.google.com/search?q=");
```

### Tambah Quick Access Site
Di `MainActivity.java`, tambahkan entry di array `QUICK_SITES`:
```java
{"Tokopedia", "https://www.tokopedia.com", "#42B549"},
```

### Ganti Warna Tema
Edit `res/values/colors.xml` sesuai selera.

---

Dibuat dengan ❤️ menggunakan Claude AI
