# Praktikum Flutter API CRUD

Proyek ini merupakan implementasi penuh fitur **CRUD (Create, Read, Update, Delete)** menggunakan Web API dari https://reqres.in.  
Aplikasi memungkinkan pengguna untuk melihat, menambahkan, mengubah, dan menghapus data user melalui komunikasi REST API.

---

## ✨ Fitur Utama

| Fitur | Status | Keterangan |
|------|:----:|------------|
| Read | ✅ | Menampilkan daftar user dari API |
| Create | ✅ | Tambah user via form dengan validasi |
| Update | ✅ | Edit data user dengan PUT Request |
| Delete | ✅ | Hapus user dengan konfirmasi dialog |
| Hero Animation | ✅ | Animasi avatar user |
| Loading & Error Handling | ✅ | UI responsif saat request API |
| Refactoring Komponen | ✅ | Widget terpisah sehingga kode bersih |

---

## 🎯 Tujuan Praktikum

1. Memahami konsep komunikasi client–server melalui REST API.
2. Mampu mengimplementasikan CRUD menggunakan **HTTP Request**.
3. Menggunakan **FutureBuilder**, **Form Validation**, dan **State Management sederhana**.
4. Menerapkan struktur kode Flutter yang baik (refactor & reusable widget).

---

## 🧠 Dasar Teori

### 🔹 REST API
REST (Representational State Transfer) adalah gaya arsitektur komunikasi client-server berbasis HTTP.

### 🔹 JSON
Format data yang dikirim API, mudah dipahami dan diproses oleh Flutter:
```json
{
  "name": "Taruna",
  "job": "Developer"
}
```

🔹 HTTP Package

Digunakan untuk request:

GET → mengambil data

POST → membuat data

PUT → memperbarui data

DELETE → menghapus data

Teknis Implementasi
Model
``` dart
class User {
  final int id;
  final String email, firstName, lastName, avatar;

  User({
    required this.id,
    required this.email,
    required this.firstName,
    required this.lastName,
    required this.avatar,
  });

  factory User.fromJson(Map<String, dynamic> json) => User(
        id: json['id'],
        email: json['email'],
        firstName: json['first_name'],
        lastName: json['last_name'],
        avatar: json['avatar'],
      );
}
```
Service API (HTTP Request)
``` dart
final String baseUrl = "https://reqres.in/api";

// GET
Future<List<User>> fetchUsers() async { ... }

// POST
Future<Map<String, dynamic>> createUser(String name, String job) async { ... }

// PUT
Future<Map<String, dynamic>> updateUser(String id, String name, String job) async { ... }

// DELETE
Future<void> deleteUser(String id) async { ... }
```
UI Screens
| File                  | Fungsi                      |
| --------------------- | --------------------------- |
| `main.dart`           | Daftar user + navigasi CRUD |
| `add_user_page.dart`  | Form Create                 |
| `edit_user_page.dart` | Form Update                 |
| `user_list_item.dart` | Widget kartu user           |
| `api_service.dart`    | Komunikasi HTTP             |

Validasi & Error Handling

✔ Validasi form input kosong
✔ Pesan error API muncul sebagai SnackBar
✔ Loading indicator saat request berjalan
contoh
``` dart
if (_isLoading)
  const CircularProgressIndicator();
```
# Analisis Kode
## Keunggulan

Struktur kode modular & mudah dikembangkan

Ramah pengguna dengan animasi dan dialog

Menggunakan pola async/await yang efisien

## Keterbatasan

Data tidak benar-benar berubah di server Reqres (mock API)

Tidak ada database lokal (opsional jika dikembangkan)

# Kesimpulan

1. CRUD API berhasil diimplementasikan dalam aplikasi Flutter.

2. Pemahaman REST, JSON, dan HTTP berhasil diaplikasikan.

3. UI aplikasi sudah memenuhi best practice untuk pengalaman pengguna.

4. Aplikasi dapat dikembangkan lebih lanjut menggunakan backend sendiri.

## Dokumentasi

<img width="654" height="1454" alt="image" src="https://github.com/user-attachments/assets/fbf4a3da-aeb4-4177-8d0f-7597ea255a95" />
<img width="654" height="1454" alt="image" src="https://github.com/user-attachments/assets/95bd5031-db71-4197-ac63-6743658e5038" />
<img width="654" height="1454" alt="image" src="https://github.com/user-attachments/assets/0e635349-d8f7-4dd9-a35e-83e13b75ff27" />
