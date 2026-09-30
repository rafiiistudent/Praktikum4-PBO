Praktikum 4 - Array, List, Iterator

Nama: Rafi Nazwan Maulana
NIM: L0325042
Program Studi: S-1 Informatika
Modul: 04 - Array, List, Iterator

Source Code

AsetIT.java

package praktikum4.tugas;

public class AsetIT {
    String idAset;
    String namaPerangkat;
    String lokasi;
    String statusKondisi;

    public AsetIT(String idAset, String namaPerangkat, String lokasi, String statusKondisi) {
        this.idAset = idAset;
        this.namaPerangkat = namaPerangkat;
        this.lokasi = lokasi;
        this.statusKondisi = statusKondisi;
    }

    public void tampilkanInfoAset() {
        System.out.println(idAset + " | " + namaPerangkat + " | " + lokasi + " | " + statusKondisi + " |");
    }
}

ManajemenAset.java

package praktikum4.tugas;

import java.util.ArrayList;
import java.util.Iterator;

public class ManajemenAset {
    ArrayList<AsetIT> daftarAset = new ArrayList<>();

    public void tambahAset(AsetIT asetBaru) {
        daftarAset.add(asetBaru);
    }

    public void tampilkanSemuaAset() {
        for (AsetIT aset : daftarAset) {
            aset.tampilkanInfoAset();
        }
    }

    public void hapusAset(String idAset) {
        Iterator<AsetIT> iterator = daftarAset.iterator();
        boolean ditemukan = false;

        while (iterator.hasNext()) {
            AsetIT aset = iterator.next();

            if (aset.idAset.equals(idAset)) {
                iterator.remove();
                ditemukan = true;
                System.out.println("Aset dengan ID " + idAset + " berhasil diremove.");
                break;
            }
        }

        if (!ditemukan) {
            System.out.println("Aset dengan ID " + idAset + " tidak ditemukan.");
        }
    }
}

MainAset.java

package praktikum4.tugas;

public class MainAset {
    public static void main(String[] args) {
        ManajemenAset manage = new ManajemenAset();

        System.out.println("------ CREATE ------");
        manage.tambahAset(new AsetIT(
                "SVR-001", "Server HP ProLiant", "Ruang Server Utama", "Baik"));
        manage.tambahAset(new AsetIT(
                "RTR-001", "Router Cisco", "Lantai 1 - Rack A", "Baik"));
        manage.tambahAset(new AsetIT(
                "SWT-001", "Switch TP-Link", "Lantai 2 - Rack B", "Rusak"));
        manage.tambahAset(new AsetIT(
                "PC-001", "PC Lenovo ThinkCentre", "Lab Komputer", "Baik"));

        System.out.println("\n--- TAMPILKAN SEMUA ASET ---");
        manage.tampilkanSemuaAset();

        System.out.println("------ DELETE ------");
        manage.hapusAset("AHR5");

        System.out.println("\n--- TAMPILKAN SEMUA ASET TERBARU ---");
        manage.tampilkanSemuaAset();
    }
}

Penjelasan Kode

AsetIT.java

Class AsetIT digunakan untuk menyimpan data setiap aset IT melalui atribut idAset, namaPerangkat, lokasi, dan statusKondisi. Constructor digunakan untuk mengisi seluruh atribut ketika objek dibuat. Method tampilkanInfoAset() digunakan untuk menampilkan seluruh informasi aset ke konsol.

ManajemenAset.java

Class ManajemenAset digunakan untuk mengelola kumpulan objek AsetIT menggunakan ArrayList<AsetIT> bernama daftarAset. Method tambahAset() digunakan untuk menambahkan objek aset baru ke dalam daftar menggunakan add(). Method tampilkanSemuaAset() digunakan untuk menampilkan seluruh data dengan perulangan For-Each dan memanggil method tampilkanInfoAset(). Method hapusAset() menggunakan Iterator untuk memeriksa aset satu per satu berdasarkan idAset. Pemeriksaan dilakukan menggunakan hasNext() dan next(), kemudian aset yang ID-nya sesuai dihapus menggunakan remove(). Jika ID tidak ditemukan, program menampilkan pesan bahwa aset tidak ditemukan.

MainAset.java

Class MainAset merupakan class utama yang digunakan untuk menjalankan program. Program membuat objek ManajemenAset, kemudian menambahkan empat aset IT, yaitu Server dengan ID SVR-001, Router dengan ID RTR-001, Switch dengan ID SWT-001, dan PC dengan ID PC-001. Setelah itu, seluruh aset ditampilkan menggunakan tampilkanSemuaAset(). Program kemudian mencoba menghapus aset dengan ID AHR5, tetapi ID tersebut tidak terdapat dalam daftar sehingga program menampilkan pesan bahwa aset tidak ditemukan. Terakhir, seluruh aset ditampilkan kembali untuk melihat kondisi daftar setelah proses penghapusan.