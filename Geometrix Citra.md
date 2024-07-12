
# Geometrix Citra
### Import Library

```bash
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
- import cv2: Ini mengimpor pustaka OpenCV, yang digunakan untuk pemrosesan gambar. OpenCV menyediakan alat untuk memanipulasi gambar dan video, termasuk membaca, menulis, dan melakukan transformasi lainnya.

- import numpy as np: Ini mengimpor pustaka NumPy, yang digunakan untuk komputasi numerik. NumPy menyediakan dukungan untuk array, matriks, dan banyak fungsi matematika lainnya.

- import matplotlib.pyplot as plt: Ini mengimpor modul pyplot dari pustaka Matplotlib, yang digunakan untuk plotting dan visualisasi data. Matplotlib dapat membuat visualisasi statis, animasi, dan interaktif di Python.

### Memuat Gambar Asli
```bash
original_image = cv2.imread('putri.jpg')
```
Kode original_image = cv2.imread('putri.jpg') digunakan untuk membaca gambar dengan nama file 'putri.jpg' menggunakan OpenCV. cv2.imread('putri.jpg') adalah fungsi dari pustaka OpenCV yang mengambil gambar dari file yang ditentukan dan memuatnya ke dalam variabel original_image. Setelah eksekusi baris ini, original_image akan berisi representasi gambar dalam bentuk array NumPy, di mana setiap elemen array mewakili nilai piksel gambar sesuai dengan format yang dibaca oleh OpenCV (biasanya dalam format BGR).

### Menampilkan Gambar Asli
```bash
plt.subplot(2, 3, 1)
plt.imshow(cv2.cvtColor(original_image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
```
- plt.subplot(2, 3, 1): Ini membuat subplot dengan ukuran grid 2x3 dan menempatkan plot pertama di posisi 1 (di baris pertama, kolom pertama).

- plt.imshow(cv2.cvtColor(original_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah dibaca (original_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Karena Matplotlib mengharapkan format RGB untuk tampilan yang benar, kita perlu melakukan konversi ini.

- plt.title('Original Image'): Ini menetapkan judul 'Original Image' untuk subplot yang pertama.

### Memutar Gambar 45 Derajat
```bash
(height, width) = original_image.shape[:2]
center = (width // 2, height // 2)
rotation_matrix = cv2.getRotationMatrix2D(center, 45, 1.0)
rotated_image = cv2.warpAffine(original_image, rotation_matrix, (width, height))
plt.subplot(2, 3, 2)
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
plt.title('Rotated Image')
```
- height, width = original_image.shape[:2]: Baris ini mengambil dimensi tinggi (height) dan lebar (width) dari gambar original_image. .shape mengembalikan tuple yang berisi (tinggi, lebar, jumlah saluran warna) dari gambar, dan [:2] mengambil hanya dua elemen pertama, yaitu tinggi dan lebar.

- center = (width // 2, height // 2): Ini menghitung titik pusat untuk rotasi. Pusat rotasi diatur ke titik tengah gambar menggunakan koordinat (width // 2, height // 2)

- rotation_matrix = cv2.getRotationMatrix2D(center, 45, 1.0): Fungsi cv2.getRotationMatrix2D digunakan untuk menghasilkan matriks rotasi untuk memutar gambar. Argumen center adalah titik pusat rotasi, 45 adalah sudut rotasi (di sini, 45 derajat searah jarum jam), dan 1.0 adalah faktor skala (di sini, tanpa perubahan skala).

- rotated_image = cv2.warpAffine(original_image, rotation_matrix, (width, height)): Fungsi cv2.warpAffine mengaplikasikan transformasi affin (termasuk rotasi) ke gambar original_image menggunakan matriks rotasi (rotation_matrix). (width, height) adalah ukuran gambar hasil yang diinginkan setelah rotasi.

- plt.subplot(2, 3, 2): Ini membuat subplot kedua dalam grid 2x3 dan menempatkan plot di posisi 2 (di baris pertama, kolom kedua).

- plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah diputar (rotated_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Karena Matplotlib memerlukan format RGB untuk tampilan yang benar, kita perlu melakukan konversi ini.

- plt.title('Rotated Image'): Ini menetapkan judul 'Rotated Image' untuk subplot kedua.

### Mengubah Ukuran Gambar 
```bash
resized_image = cv2.resize(original_image, (original_image.shape[1]//3, original_image.shape[0]//2))
plt.subplot(2, 3, 3)
plt.imshow(cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB))
plt.title('Resized Image')
```
- resized_image = cv2.resize(original_image, (original_image.shape[1]//3, original_image.shape[0]//2)): Fungsi cv2.resize digunakan untuk meresize gambar original_image. Argumen pertama adalah gambar yang ingin diresize, dan argumen kedua adalah ukuran yang diinginkan untuk gambar hasil, disini (original_image.shape[1]//3, original_image.shape[0]//2) mengindikasikan bahwa lebar gambar baru akan menjadi sepertiga dari lebar gambar asli, dan tinggi gambar baru akan menjadi setengah dari tinggi gambar asli.

- plt.subplot(2, 3, 3): Ini membuat subplot ketiga dalam grid 2x3 dan menempatkan plot di posisi 3 (di baris pertama, kolom ketiga).

- plt.imshow(cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah diresize (resized_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Konversi ini diperlukan karena Matplotlib mengharapkan format RGB untuk tampilan yang benar.

- plt.title('Resized Image'): Ini menetapkan judul 'Resized Image' untuk subplot ketiga.

### Memotong Gambar ke Bagian Tertentu

```bash
cropped_image = original_image[0:original_image.shape[0]//2, 0:original_image.shape[1]//2]
plt.subplot(2, 3, 4)
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title('Cropped Image')
```
- cropped_image = original_image[0:original_image.shape[0]//2, 0:original_image.shape[1]//2]: Ini adalah operasi slicing pada array NumPy (representasi gambar dalam OpenCV). Di sini, original_image[0:original_image.shape[0]//2, 0:original_image.shape[1]//2] memotong gambar menjadi setengah tinggi dan setengah lebar dari gambar asli. Artinya, gambar baru akan memiliki ukuran yang hanya setengah tinggi dan setengah lebar dari gambar asli.

- plt.subplot(2, 3, 4): Ini membuat subplot keempat dalam grid 2x3 dan menempatkan plot di posisi 4 (di baris kedua, kolom pertama).

- plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah dipotong (cropped_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Konversi ini diperlukan karena Matplotlib mengharapkan format RGB untuk tampilan yang benar.

- plt.title('Cropped Image'): Ini menetapkan judul 'Cropped Image' untuk subplot keempat.

### Membalik Gambar Secara Horizontal
```bash
flipped_image = cv2.flip(original_image, 1)
plt.subplot(2, 3, 5)
plt.imshow(cv2.cvtColor(flipped_image, cv2.COLOR_BGR2RGB))
plt.title('Flipped Image')
```
- flipped_image = cv2.flip(original_image, 1): Fungsi cv2.flip digunakan untuk melakukan flipping (pembalikan) gambar. Argumen pertama adalah gambar yang ingin dibalik, yaitu original_image, dan argumen kedua (1) menentukan arah flipping. Di sini, nilai 1 mengindikasikan flipping horizontal.

- plt.subplot(2, 3, 5): Ini membuat subplot kelima dalam grid 2x3 dan menempatkan plot di posisi 5 (di baris kedua, kolom kedua).

- plt.imshow(cv2.cvtColor(flipped_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah dibalik (flipped_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Konversi ini diperlukan karena Matplotlib mengharapkan format RGB untuk tampilan yang benar.

- plt.title('Flipped Image'): Ini menetapkan judul 'Flipped Image' untuk subplot kelima.

### Translated Gambar 
```bash
rows, cols = original_image.shape[:2]
translation_matrix = np.float32([[1, 0, 250], [0, 1, 180]])
translated_image = cv2.warpAffine(original_image, translation_matrix, (cols, rows))
plt.subplot(2, 3, 6)
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
plt.title('Translated Image')
```
- rows, cols = original_image.shape[:2]: Baris ini mengambil dimensi tinggi (rows) dan lebar (cols) dari gambar original_image. .shape mengembalikan tuple yang berisi (tinggi, lebar, jumlah saluran warna) dari gambar.

- translation_matrix = np.float32([[1, 0, 250], [0, 1, 180]]): Matriks translasi digunakan untuk memindahkan gambar. np.float32 digunakan untuk membuat matriks dalam format float32 yang diperlukan oleh OpenCV. Matriks ini memiliki format [1, 0, tx] untuk translasi horizontal (tx adalah jumlah piksel yang digeser secara horizontal) dan [0, 1, ty] untuk translasi vertikal (ty adalah jumlah piksel yang digeser secara vertikal). Di sini, kita translasi gambar sebanyak 250 piksel ke kanan dan 180 piksel ke bawah.

- translated_image = cv2.warpAffine(original_image, translation_matrix, (cols, rows)): Fungsi cv2.warpAffine mengaplikasikan transformasi affin (termasuk translasi) ke gambar original_image menggunakan matriks translasi (translation_matrix). (cols, rows) adalah ukuran gambar hasil yang diinginkan setelah translasi.

- plt.subplot(2, 3, 6): Ini membuat subplot keenam dalam grid 2x3 dan menempatkan plot di posisi 6 (di baris kedua, kolom ketiga).

- plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB)): Ini menampilkan gambar yang telah diterjemahkan (translated_image) setelah dikonversi dari format BGR (format default OpenCV) ke RGB (format default Matplotlib). Konversi ini diperlukan karena Matplotlib mengharapkan format RGB untuk tampilan yang benar.

- plt.title('Translated Image'): Ini menetapkan judul 'Translated Image' untuk subplot keenam.

### Menampilkan Tata Letak Subplot 
```bash
plt.tight_layout()
plt.show()
```
Perintah plt.tight_layout() digunakan untuk secara otomatis menyesuaikan tata letak subplot agar sesuai dan rapi sebelum menampilkan plot menggunakan plt.show() dalam Matplotlib. Ini membantu menghindari tumpang tindih antara subplot dan memastikan bahwa visualisasi yang dihasilkan terlihat lebih baik.


### Teori Pendukung
Berikut adalah beberapa teori pendukung untuk program diatas:
1. OpenCV (Open Source Computer Vision Library):
- Fungsi Dasar: OpenCV menyediakan fungsi dasar untuk membaca, menulis, dan memanipulasi gambar. Contohnya adalah cv2.imread() untuk membaca gambar dari file dan cv2.imwrite() untuk menulis gambar ke file.
- Transformasi Gambar: Seperti rotasi (cv2.getRotationMatrix2D() dan cv2.warpAffine()), resizing (cv2.resize()), flipping (cv2.flip()), dan translasi (cv2.warpAffine()).

2. NumPy:
- Array dan Operasi Numerik: NumPy digunakan untuk merepresentasikan gambar sebagai array multidimensi, yang memungkinkan manipulasi yang efisien seperti slicing untuk cropping gambar dan perhitungan matematis untuk transformasi geometris.

3. Matplotlib:
- Visualisasi: Matplotlib digunakan untuk menampilkan gambar yang telah dimanipulasi atau dianalisis. Ini mencakup plot untuk menampilkan gambar asli, gambar yang diputar, diresize, dipotong, dibalik, dan diterjemahkan seperti yang Anda lakukan dalam proyek Anda.

4. Subplotting: 
- plt.subplot() digunakan untuk mengatur tata letak subplot, yang berguna untuk menampilkan beberapa gambar atau plot dalam satu jendela visualisasi.

5. Konsep Geometri Transformasi:
- Rotasi: Transformasi rotasi digunakan untuk memutar gambar terhadap pusat tertentu, dengan sudut rotasi tertentu.
- Resizing: Mengubah ukuran gambar untuk memperbesar atau memperkecil gambar sesuai dengan kebutuhan aplikasi.
- Cropping: Memotong bagian tertentu dari gambar, yang berguna untuk fokus pada area tertentu atau mengubah komposisi visual.
- Flipping: Melakukan pembalikan horizontal atau vertikal gambar untuk efek visual atau persyaratan lainnya.
- Translasi: Memindahkan gambar ke posisi baru berdasarkan vektor translasi yang diberikan.
