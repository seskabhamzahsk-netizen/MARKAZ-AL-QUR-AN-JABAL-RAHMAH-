<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Markaz Al-Qur'an Jabal Rahmah</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            /* Warna sesuai brand Markaz Al-Qur'an Jabal Rahmah (biru-kuning-putih) */
            --biru-tua: #0d3b66;
            --biru: #1e4e8c;
            --biru-muda: #3a7bd5;
            --kuning: #f5a91e;
            --kuning-muda: #ffd166;
            --putih: #ffffff;
            --abu: #f8f9fa;
            --abu-muda: #e9ecef;
            --hijau: #06d6a0;
            --biru-absen: #118ab2;
            --kuning-absen: #ffd166;
            --merah: #ef476f;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #f0f4f8, #e6f0fa);
            color: #2d3748;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: linear-gradient(135deg, var(--biru-tua), var(--biru));
            color: var(--putih);
            padding: 2rem;
            text-align: center;
            border-radius: 16px;
            margin-bottom: 2rem;
            box-shadow: 0 6px 20px rgba(13, 59, 102, 0.25);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "";
            position: absolute;
            top: -50px;
            right: -50px;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, var(--kuning) 0%, transparent 70%);
            opacity: 0.2;
            border-radius: 50%;
        }

        header h1 {
            font-size: 2.4rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
            letter-spacing: -0.5px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }

        header p {
            font-size: 1.2rem;
            opacity: 0.95;
            max-width: 700px;
            margin: 0 auto;
            line-height: 1.6;
        }

        /* Halaman management */
        .halaman {
            display: none;
            animation: fadeIn 0.5s ease;
        }

        .halaman.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Program Selection */
        .program-selection {
            display: flex;
            flex-wrap: wrap;
            gap: 24px;
            justify-content: center;
            margin-top: 20px;
        }

        .program-card {
            background: var(--putih);
            border-radius: 20px;
            padding: 32px 24px;
            width: 300px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(30, 78, 140, 0.15);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            cursor: pointer;
            border: 2px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .program-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: var(--biru);
        }

        .program-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 15px 40px rgba(13, 59, 102, 0.25);
            border-color: var(--biru);
        }

        .program-card i {
            font-size: 3.2rem;
            color: var(--biru);
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--biru), var(--biru-muda));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .program-card h3 {
            font-size: 1.5rem;
            color: var(--biru-tua);
            margin-bottom: 16px;
            font-weight: 700;
        }

        .program-card p {
            font-size: 1rem;
            color: #4a5568;
            line-height: 1.6;
        }

        /* Navigation buttons */
        .nav-bar {
            text-align: center;
            margin: 25px 0;
        }

        .nav-btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: var(--biru);
            color: white;
            border: none;
            padding: 14px 32px;
            font-size: 1.1rem;
            font-weight: 600;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 12px rgba(30, 78, 140, 0.3);
        }

        .nav-btn:hover {
            background: var(--biru-tua);
            transform: translateY(-3px);
            box-shadow: 0 6px 16px rgba(13, 59, 102, 0.4);
        }

        .nav-btn i {
            font-size: 1.2rem;
        }

        /* Form Section */
        .form-section {
            background: var(--putih);
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 10px 30px rgba(13, 59, 102, 0.1);
            margin-bottom: 2rem;
        }

        .form-title {
            font-size: 1.8rem;
            color: var(--biru-tua);
            margin-bottom: 1.8rem;
            text-align: center;
            font-weight: 800;
            position: relative;
        }

        .form-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--kuning);
            margin: 12px auto 0;
            border-radius: 2px;
        }

        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group.full {
            grid-column: 1 / -1;
        }

        label {
            display: block;
            margin-bottom: 0.75rem;
            font-weight: 700;
            color: var(--biru-tua);
            font-size: 1.05rem;
        }

        input, select, textarea {
            width: 100%;
            padding: 14px 18px;
            border: 2px solid #cbd5e0;
            border-radius: 12px;
            font-size: 1.05rem;
            transition: all 0.3s;
            background: #fafbff;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--biru);
            box-shadow: 0 0 0 4px rgba(30, 78, 140, 0.15);
            background: white;
        }

        .btn {
            background: linear-gradient(135deg, var(--biru), var(--biru-tua));
            color: white;
            border: none;
            padding: 16px 32px;
            font-size: 1.15rem;
            font-weight: 700;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
            margin-top: 1.5rem;
            box-shadow: 0 4px 15px rgba(13, 59, 102, 0.2);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(13, 59, 102, 0.3);
            background: linear-gradient(135deg, var(--biru-tua), #0a2e55);
        }

        .success-message {
            display: none;
            background: linear-gradient(135deg, #e6f7ee, #d1f0e0);
            border-left: 5px solid var(--hijau);
            padding: 24px;
            border-radius: 12px;
            margin-top: 2rem;
            text-align: center;
            animation: slideIn 0.5s ease;
        }

        .success-message.show {
            display: block;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Absensi Section */
        .absensi-section {
            background: var(--putih);
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 10px 30px rgba(13, 59, 102, 0.1);
        }

        .tabs {
            display: flex;
            gap: 2px;
            background: var(--abu-muda);
            border-radius: 12px;
            overflow: hidden;
            margin-bottom: 2rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .tab-btn {
            flex: 1;
            padding: 16px;
            background: white;
            border: none;
            font-weight: 700;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s;
            color: #4a5568;
        }

        .tab-btn.active {
            background: var(--biru);
            color: white;
        }

        .filter-container {
            display: flex;
            gap: 15px;
            justify-content: center;
            flex-wrap: wrap;
            margin-bottom: 24px;
        }

        .filter-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .filter-label {
            font-weight: 700;
            color: var(--biru-tua);
        }

        .filter-select {
            padding: 12px 16px;
            border: 2px solid #cbd5e0;
            border-radius: 12px;
            font-size: 1.05rem;
            background: #fafbff;
            min-width: 180px;
        }

        .pekan-selector {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-bottom: 24px;
        }

        .pekan-btn {
            padding: 10px 20px;
            background: var(--abu);
            border: none;
            border-radius: 10px;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s;
            min-width: 130px;
        }

        .pekan-btn.active, .pekan-btn:hover {
            background: var(--kuning);
            color: var(--biru-tua);
            transform: translateY(-2px);
        }

        .add-row-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background: var(--kuning);
            color: var(--biru-tua);
            border: none;
            padding: 14px 28px;
            font-weight: 700;
            font-size: 1.1rem;
            border-radius: 12px;
            cursor: pointer;
            margin: 20px auto;
            width: fit-content;
            box-shadow: 0 4px 12px rgba(245, 169, 30, 0.3);
            transition: all 0.3s;
        }

        .add-row-btn:hover {
            background: #e59e0e;
            transform: translateY(-3px);
            box-shadow: 0 6px 16px rgba(245, 169, 30, 0.4);
        }

        .absen-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1.5rem;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 6px 20px rgba(13, 59, 102, 0.08);
        }

        .absen-table th {
            background: var(--biru);
            color: white;
            font-weight: 700;
            font-size: 1.1rem;
            padding: 16px 12px;
            text-align: center;
        }

        .absen-table td {
            padding: 16px 12px;
            text-align: center;
            border-bottom: 1px solid #edf2f7;
            background: white;
        }

        .absen-table tbody tr:nth-child(even) {
            background-color: #fafbff;
        }

        .absen-table tbody tr:last-child td {
            border-bottom: none;
        }

        .absen-select {
            width: 100%;
            padding: 10px;
            border-radius: 8px;
            border: 2px solid #cbd5e0;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
        }

        .absen-hadir { 
            background-color: var(--hijau); 
            color: white; 
            border-color: #05c994;
        }
        .absen-izin { 
            background-color: var(--biru-absen); 
            color: white; 
            border-color: #0f7aa6;
        }
        .absen-sakit { 
            background-color: var(--kuning-absen); 
            color: #333; 
            border-color: #e6bd4a;
        }
        .absen-alfa { 
            background-color: var(--merah); 
            color: white; 
            border-color: #e03e5f;
        }

        .persentase-cell {
            font-weight: 700;
            font-size: 1.1rem;
        }

        .persentase-hadir { color: var(--hijau); }
        .persentase-cukup { color: var(--kuning); }
        .persentase-rendah { color: var(--merah); }

        .hapus-baris {
            background: var(--merah);
            color: white;
            border: none;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .hapus-baris:hover {
            background: #d62c57;
            transform: scale(1.1);
        }

        /* Data Santri Section */
        .data-santri-section {
            background: var(--putih);
            border-radius: 20px;
            padding: 2.5rem;
            box-shadow: 0 10px 30px rgba(13, 59, 102, 0.1);
            margin-top: 2rem;
        }

        .search-bar {
            display: flex;
            gap: 12px;
            margin-bottom: 24px;
            flex-wrap: wrap;
        }

        .search-bar input {
            flex: 1;
            min-width: 300px;
        }

        .santri-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1.5rem;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 6px 20px rgba(13, 59, 102, 0.08);
        }

        .santri-table th {
            background: var(--biru);
            color: white;
            font-weight: 700;
            padding: 16px 12px;
            text-align: left;
        }

        .santri-table td {
            padding: 16px 12px;
            border-bottom: 1px solid #edf2f7;
            background: white;
        }

        .santri-table tbody tr:nth-child(even) {
            background-color: #fafbff;
        }

        .santri-table tbody tr:last-child td {
            border-bottom: none;
        }

        .level-badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-weight: 700;
            font-size: 0.9rem;
        }

        .level-1 { background: #dbeafe; color: #1d4ed8; }
        .level-2 { background: #dcfce7; color: #16a34a; }
        .level-3 { background: #ffedd5; color: #ea580c; }
        .level-4 { background: #fde68a; color: #ca8a04; }

        .footer {
            text-align: center;
            margin-top: 3rem;
            padding: 2rem;
            color: #64748b;
            font-size: 1rem;
            border-top: 1px solid #e2e8f0;
        }

        @media (max-width: 768px) {
            .form-grid {
                grid-template-columns: 1fr;
            }
            .program-card {
                width: 100%;
            }
            header h1 {
                font-size: 1.9rem;
            }
            .filter-group {
                flex-direction: column;
                align-items: stretch;
            }
            .filter-select {
                min-width: 100%;
            }
            .bulan-btn, .pekan-btn {
                min-width: 120px;
                padding: 10px 16px;
                font-size: 0.95rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Markaz Al-Qur'an Jabal Rahmah</h1>
            <p>Pusat Pendidikan Al-Qur'an Terpadu - Mencetak Generasi Qur'ani</p>
        </header>

        <!-- HALAMAN UTAMA: PILIH PROGRAM -->
        <div id="halaman-utama" class="halaman active">
            <h2 style="text-align: center; margin-bottom: 1.8rem; color: var(--biru-tua); font-size: 2rem; font-weight: 800;">Pilih Program</h2>
            <div class="program-selection">
                <div class="program-card" data-program="tpq">
                    <i class="fas fa-book-open"></i>
                    <h3>Taman Pendidikan Al-Qur'an</h3>
                    <p>Untuk anak usia 5-12 tahun</p>
                </div>
                <div class="program-card" data-program="dewasa">
                    <i class="fas fa-user-graduate"></i>
                    <h3>Kelas Dewasa</h3>
                    <p>Tahsin & Dirosa Al-Qur'an</p>
                </div>
                <div class="program-card" data-program="tahfiz">
                    <i class="fas fa-mosque"></i>
                    <h3>Tahfiz Weekend</h3>
                    <p>Hafalan intensif akhir pekan</p>
                </div>
            </div>
        </div>

        <!-- HALAMAN PROGRAM: PILIH MENU -->
        <div id="halaman-program" class="halaman">
            <div class="nav-bar">
                <button class="nav-btn" id="btn-kembali-utama">
                    <i class="fas fa-arrow-left"></i> Kembali ke Program
                </button>
            </div>
            
            <h2 id="judul-program" style="text-align: center; margin-bottom: 1.8rem; color: var(--biru-tua); font-size: 2rem; font-weight: 800;">...</h2>
            
            <div class="program-selection">
                <div class="program-card" data-aksi="pendaftaran">
                    <i class="fas fa-file-signature"></i>
                    <h3>Pendaftaran</h3>
                    <p>Daftar santri baru</p>
                </div>
                <div class="program-card" data-aksi="absensi">
                    <i class="fas fa-clipboard-list"></i>
                    <h3>Absensi</h3>
                    <p>Isi kehadiran santri</p>
                </div>
                <div class="program-card" data-aksi="data-santri">
                    <i class="fas fa-users"></i>
                    <h3>Data Santri</h3>
                    <p>Daftar santri terdaftar</p>
                </div>
            </div>
        </div>

        <!-- HALAMAN PENDAFTARAN -->
        <div id="halaman-pendaftaran" class="halaman">
            <div class="nav-bar">
                <button class="nav-btn" id="btn-kembali-program">
                    <i class="fas fa-arrow-left"></i> Kembali ke Menu
                </button>
            </div>
            
            <div class="form-section">
                <h2 class="form-title" id="form-judul">...</h2>
                
                <!-- TPQ Form -->
                <form id="tpq-form" style="display: none;">
                    <div class="form-grid">
                        <div class="form-group">
                            <label for="tpq-nama">Nama Santri</label>
                            <input type="text" id="tpq-nama" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-tgl-lahir">Tanggal Lahir</label>
                            <input type="date" id="tpq-tgl-lahir" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-jenis-kelamin">Jenis Kelamin</label>
                            <select id="tpq-jenis-kelamin" required>
                                <option value="">Pilih</option>
                                <option value="L">Laki-laki</option>
                                <option value="P">Perempuan</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="tpq-kelas">Kelas & Asal Sekolah</label>
                            <input type="text" id="tpq-kelas" placeholder="Contoh: Kelas 3 SDN 1 Bandung" required>
                        </div>
                        <div class="form-group full">
                            <label for="tpq-nama-ayah">Nama Ayah</label>
                            <input type="text" id="tpq-nama-ayah" required>
                        </div>
                        <div class="form-group full">
                            <label for="tpq-nama-ibu">Nama Ibu</label>
                            <input type="text" id="tpq-nama-ibu" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-pekerjaan-ayah">Pekerjaan Ayah</label>
                            <input type="text" id="tpq-pekerjaan-ayah" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-pekerjaan-ibu">Pekerjaan Ibu</label>
                            <input type="text" id="tpq-pekerjaan-ibu" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-no-ayah">No. HP Ayah</label>
                            <input type="tel" id="tpq-no-ayah" required>
                        </div>
                        <div class="form-group">
                            <label for="tpq-no-ibu">No. HP Ibu</label>
                            <input type="tel" id="tpq-no-ibu" required>
                        </div>
                        <div class="form-group full">
                            <label for="tpq-alamat">Alamat</label>
                            <textarea id="tpq-alamat" rows="3" required></textarea>
                        </div>
                        <div class="form-group full">
                            <label for="tpq-metode">Metode yang Pernah Dipakai</label>
                            <input type="text" id="tpq-metode" placeholder="Contoh: UMMI, Qiroati, dll">
                        </div>
                        <div class="form-group">
                            <label for="tpq-level">Level</label>
                            <select id="tpq-level" required>
                                <option value="">Pilih Level</option>
                                <option value="1">Level 1 (Pemula)</option>
                                <option value="2">Level 2 (Menengah)</option>
                                <option value="3">Level 3 (Lanjut)</option>
                                <option value="4">Level 4 (Tahfiz)</option>
                            </select>
                        </div>
                    </div>
                    <button type="submit" class="btn">Daftar Sekarang</button>
                </form>

                <!-- Dewasa Form -->
                <form id="dewasa-form" style="display: none;">
                    <div class="form-grid">
                        <div class="form-group">
                            <label for="dewasa-nama">Nama Lengkap</label>
                            <input type="text" id="dewasa-nama" required>
                        </div>
                        <div class="form-group">
                            <label for="dewasa-tgl-lahir">Tanggal Lahir</label>
                            <input type="date" id="dewasa-tgl-lahir" required>
                        </div>
                        <div class="form-group">
                            <label for="dewasa-alamat">Alamat</label>
                            <input type="text" id="dewasa-alamat" required>
                        </div>
                        <div class="form-group">
                            <label for="dewasa-jk">Jenis Kelamin</label>
                            <select id="dewasa-jk" required>
                                <option value="">Pilih</option>
                                <option value="L">Laki-laki</option>
                                <option value="P">Perempuan</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="dewasa-pekerjaan">Pekerjaan</label>
                            <input type="text" id="dewasa-pekerjaan" required>
                        </div>
                        <div class="form-group">
                            <label for="dewasa-no-hp">No. HP</label>
                            <input type="tel" id="dewasa-no-hp" required>
                        </div>
                        <div class="form-group full">
                            <label for="dewasa-level">Level</label>
                            <select id="dewasa-level" required>
                                <option value="">Pilih Level</option>
                                <option value="1">Level 1 (Pemula - Iqro')</option>
                                <option value="2">Level 2 (Menengah - Juz 30)</option>
                                <option value="3">Level 3 (Lanjut - Juz 1-10)</option>
                                <option value="4">Level 4 (Tahfiz - Juz 11-30)</option>
                            </select>
                        </div>
                        <div class="form-group full">
                            <label>Program yang Hendak Diikuti</label>
                            <div style="display: flex; gap: 1.2rem; flex-wrap: wrap;">
                                <label style="display: flex; align-items: center; gap: 8px;">
                                    <input type="checkbox" name="program-dewasa" value="tahsin" style="width: 18px; height: 18px;">
                                    Tahsin Al-Qur'an
                                </label>
                                <label style="display: flex; align-items: center; gap: 8px;">
                                    <input type="checkbox" name="program-dewasa" value="dirosa" style="width: 18px; height: 18px;">
                                    Dirosa Al-Qur'an
                                </label>
                            </div>
                        </div>
                    </div>
                    <button type="submit" class="btn">Daftar Sekarang</button>
                </form>

                <!-- Tahfiz Form (Placeholder) -->
                <div id="tahfiz-form" style="display: none; text-align: center; padding: 2.5rem; background: #f8fafc; border-radius: 16px; border: 2px dashed var(--biru);">
                    <i class="fas fa-info-circle" style="font-size: 3.5rem; color: var(--biru); margin-bottom: 1.2rem;"></i>
                    <h3 style="color: var(--biru-tua); font-size: 1.8rem; margin-bottom: 1rem;">Formulir Pendaftaran Tahfiz Weekend</h3>
                    <p style="font-size: 1.1rem; max-width: 600px; margin: 0 auto 1.5rem; line-height: 1.7;">
                        Formulir pendaftaran Tahfiz Weekend akan segera dibuka. 
                        Silakan hubungi admin Markaz Al-Qur'an Jabal Rahmah untuk informasi lebih lanjut.
                    </p>
                    <div style="background: #e0f2fe; padding: 1.2rem; border-radius: 12px; display: inline-block; margin-top: 1rem;">
                        <p style="margin: 0; font-weight: 600;"><i class="fas fa-phone"></i> Kontak Admin: 0812-3456-7890</p>
                    </div>
                </div>

                <div class="success-message" id="pendaftaran-success">
                    <i class="fas fa-check-circle" style="font-size: 2.5rem; color: var(--hijau); margin-bottom: 1.2rem;"></i>
                    <h3 style="color: var(--biru-tua); font-size: 1.6rem; margin-bottom: 0.8rem;">Data Berhasil Disimpan!</h3>
                    <p style="font-size: 1.1rem; max-width: 600px; margin: 0 auto; line-height: 1.6;">
                        Terima kasih telah mendaftar di Markaz Al-Qur'an Jabal Rahmah. 
                        Silahkan menunggu konfirmasi dari admin melalui nomor yang telah didaftarkan.
                    </p>
                </div>
            </div>
        </div>

        <!-- HALAMAN ABSENSI -->
        <div id="halaman-absensi" class="halaman">
            <div class="nav-bar">
                <button class="nav-btn" id="btn-kembali-program-absen">
                    <i class="fas fa-arrow-left"></i> Kembali ke Menu
                </button>
            </div>
            
            <div class="absensi-section">
                <h2 class="form-title" id="absen-judul">Absensi Santri - TPQ</h2>
                
                <div class="tabs">
                    <button class="tab-btn active" data-tab="input">Input Absensi</button>
                    <button class="tab-btn" data-tab="daftar">Daftar Santri</button>
                </div>

                <!-- Tab Input Manual -->
                <div id="tab-input" class="tab-content">
                    <div class="filter-container">
                        <div class="filter-group">
                            <span class="filter-label">Bulan:</span>
                            <select id="bulan-filter" class="filter-select">
                                <option value="2025-11">November 2025</option>
                                <option value="2025-12">Desember 2025</option>
                                <option value="2026-01">Januari 2026</option>
                                <option value="2026-02">Februari 2026</option>
                                <option value="2026-03">Maret 2026</option>
                                <option value="2026-04">April 2026</option>
                                <option value="2026-05">Mei 2026</option>
                            </select>
                        </div>
                        <div class="filter-group">
                            <span class="filter-label">Pekan:</span>
                            <select id="pekan-filter" class="filter-select">
                                <option value="1">Pekan 1</option>
                                <option value="2">Pekan 2</option>
                                <option value="3">Pekan 3</option>
                                <option value="4">Pekan 4</option>
                            </select>
                        </div>
                    </div>

                    <button class="add-row-btn" id="tambah-baris">
                        <i class="fas fa-plus"></i> Tambah Nama Santri
                    </button>

                    <div style="overflow-x: auto;">
                        <table class="absen-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Santri</th>
                                    <th>Senin</th>
                                    <th>Selasa</th>
                                    <th>Rabu</th>
                                    <th>Kamis</th>
                                    <th>Jumat</th>
                                    <th>Persentase</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="absen-body">
                                <!-- Rows will be added here -->
                            </tbody>
                        </table>
                    </div>

                    <button class="btn" id="simpan-absen" style="margin-top: 25px;">Simpan Absensi</button>
                </div>

                <!-- Tab Daftar Santri -->
                <div id="tab-daftar" class="tab-content" style="display: none;">
                    <div class="search-bar">
                        <input type="text" id="search-santri" placeholder="Cari nama santri...">
                        <button class="btn" style="width: auto; padding: 0 24px;">Cari</button>
                    </div>
                    <div style="overflow-x: auto;">
                        <table class="santri-table">
                            <thead>
                                <tr>
                                    <th>No</th>
                                    <th>Nama Santri</th>
                                    <th>Tanggal Lahir</th>
                                    <th>Alamat</th>
                                    <th>Level</th>
                                    <th>Program</th>
                                </tr>
                            </thead>
                            <tbody id="daftar-santri-body">
                                <!-- Data santri akan diisi di sini -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

        <!-- HALAMAN DATA SANTRI -->
        <div id="halaman-data-santri" class="halaman">
            <div class="nav-bar">
                <button class="nav-btn" id="btn-kembali-program-data">
                    <i class="fas fa-arrow-left"></i> Kembali ke Menu
                </button>
            </div>
            
            <div class="data-santri-section">
                <h2 class="form-title">Data Santri Terdaftar</h2>
                
                <div class="search-bar">
                    <input type="text" id="search-santri-2" placeholder="Cari nama santri...">
                    <select id="filter-program" class="filter-select">
                        <option value="">Semua Program</option>
                        <option value="tpq">TPQ</option>
                        <option value="dewasa">Dewasa</option>
                        <option value="tahfiz">Tahfiz</option>
                    </select>
                    <select id="filter-level" class="filter-select">
                        <option value="">Semua Level</option>
                        <option value="1">Level 1</option>
                        <option value="2">Level 2</option>
                        <option value="3">Level 3</option>
                        <option value="4">Level 4</option>
                    </select>
                    <button class="btn" style="width: auto; padding: 0 24px;">Filter</button>
                </div>
                
                <div style="overflow-x: auto;">
                    <table class="santri-table">
                        <thead>
                            <tr>
                                <th>No</th>
                                <th>Nama Santri</th>
                                <th>Tanggal Lahir</th>
                                <th>Alamat</th>
                                <th>Level</th>
                                <th>Program</th>
                            </tr>
                        </thead>
                        <tbody id="data-santri-body">
                            <!-- Data santri akan diisi di sini -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>&copy; 2025 Markaz Al-Qur'an Jabal Rahmah. All rights reserved.</p>
            <p style="margin-top: 8px; font-size: 0.95rem; color: #718096;">
                Jl. Jabal Rahmah No. 123, Bandung, Jawa Barat | Telp: (022) 1234-5678
            </p>
        </div>
    </div>

    <script>
        // Data storage
        const data = {
            tpq: [],
            dewasa: [],
            tahfiz: []
        };

        // State management
        let state = {
            program: null,
            aksi: null,
            bulanAktif: '2025-11',
            pekanAktif: '1'
        };

        // DOM Elements
        const halamanUtama = document.getElementById('halaman-utama');
        const halamanProgram = document.getElementById('halaman-program');
        const halamanPendaftaran = document.getElementById('halaman-pendaftaran');
        const halamanAbsensi = document.getElementById('halaman-absensi');
        const halamanDataSantri = document.getElementById('halaman-data-santri');
        
        const programCardsUtama = document.querySelectorAll('#halaman-utama .program-card');
        const programCardsMenu = document.querySelectorAll('#halaman-program .program-card');
        const btnKembaliUtama = document.getElementById('btn-kembali-utama');
        const btnKembaliProgram = document.getElementById('btn-kembali-program');
        const btnKembaliProgramAbsen = document.getElementById('btn-kembali-program-absen');
        const btnKembaliProgramData = document.getElementById('btn-kembali-program-data');
        
        const tpqForm = document.getElementById('tpq-form');
        const dewasaForm = document.getElementById('dewasa-form');
        const tahfizForm = document.getElementById('tahfiz-form');
        const formJudul = document.getElementById('form-judul');
        const pendaftaranSuccess = document.getElementById('pendaftaran-success');
        
        const absenJudul = document.getElementById('absen-judul');
        const absenBody = document.getElementById('absen-body');
        const tambahBarisBtn = document.getElementById('tambah-baris');
        const simpanAbsenBtn = document.getElementById('simpan-absen');
        const tabBtns = document.querySelectorAll('.tab-btn');
        const tabContents = document.querySelectorAll('.tab-content');
        
        const daftarSantriBody = document.getElementById('daftar-santri-body');
        const dataSantriBody = document.getElementById('data-santri-body');
        
        // Filter elements
        const bulanFilter = document.getElementById('bulan-filter');
        const pekanFilter = document.getElementById('pekan-filter');

        // Program names mapping
        const programNames = {
            tpq: 'Taman Pendidikan Al-Qur\'an',
            dewasa: 'Kelas Dewasa',
            tahfiz: 'Tahfiz Weekend'
        };

        // Navigation functions
        function tampilkanHalaman(halaman) {
            document.querySelectorAll('.halaman').forEach(el => {
                el.classList.remove('active');
            });
            document.getElementById('halaman-' + halaman).classList.add('active');
        }

        // Event Listeners
        programCardsUtama.forEach(card => {
            card.addEventListener('click', () => {
                state.program = card.dataset.program;
                document.getElementById('judul-program').textContent = programNames[state.program];
                tampilkanHalaman('program');
            });
        });

        programCardsMenu.forEach(card => {
            card.addEventListener('click', () => {
                state.aksi = card.dataset.aksi;
                
                if (state.aksi === 'pendaftaran') {
                    // Set form title
                    formJudul.textContent = `Pendaftaran ${programNames[state.program]}`;
                    
                    // Show appropriate form
                    tpqForm.style.display = 'none';
                    dewasaForm.style.display = 'none';
                    tahfizForm.style.display = 'none';
                    
                    if (state.program === 'tpq') {
                        tpqForm.style.display = 'block';
                    } else if (state.program === 'dewasa') {
                        dewasaForm.style.display = 'block';
                    } else if (state.program === 'tahfiz') {
                        tahfizForm.style.display = 'block';
                    }
                    
                    tampilkanHalaman('pendaftaran');
                } else if (state.aksi === 'absensi') {
                    absenJudul.textContent = `Absensi Santri - ${programNames[state.program]}`;
                    tampilkanHalaman('absensi');
                    renderAbsensiTable();
                } else if (state.aksi === 'data-santri') {
                    tampilkanHalaman('data-santri');
                    renderDataSantri();
                }
            });
        });

        btnKembaliUtama.addEventListener('click', () => {
            tampilkanHalaman('utama');
        });

        btnKembaliProgram.addEventListener('click', () => {
            tampilkanHalaman('program');
        });

        btnKembaliProgramAbsen.addEventListener('click', () => {
            tampilkanHalaman('program');
        });

        btnKembaliProgramData.addEventListener('click', () => {
            tampilkanHalaman('program');
        });

        // Form submissions
        tpqForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const santri = {
                id: Date.now(),
                nama: document.getElementById('tpq-nama').value,
                tgl_lahir: document.getElementById('tpq-tgl-lahir').value,
                jenis_kelamin: document.getElementById('tpq-jenis-kelamin').value,
                kelas: document.getElementById('tpq-kelas').value,
                ayah: document.getElementById('tpq-nama-ayah').value,
                ibu: document.getElementById('tpq-nama-ibu').value,
                pekerjaan_ayah: document.getElementById('tpq-pekerjaan-ayah').value,
                pekerjaan_ibu: document.getElementById('tpq-pekerjaan-ibu').value,
                no_ayah: document.getElementById('tpq-no-ayah').value,
                no_ibu: document.getElementById('tpq-no-ibu').value,
                alamat: document.getElementById('tpq-alamat').value,
                metode: document.getElementById('tpq-metode').value,
                level: document.getElementById('tpq-level').value,
                program: 'tpq'
            };
            
            data.tpq.push(santri);
            pendaftaranSuccess.classList.add('show');
            tpqForm.reset();
            setTimeout(() => pendaftaranSuccess.classList.remove('show'), 4000);
        });

        dewasaForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const checkboxes = document.querySelectorAll('input[name="program-dewasa"]:checked');
            const programs = Array.from(checkboxes).map(cb => cb.value);
            
            if (programs.length === 0) {
                alert('Silakan pilih minimal satu program');
                return;
            }
            
            const peserta = {
                id: Date.now(),
                nama: document.getElementById('dewasa-nama').value,
                tgl_lahir: document.getElementById('dewasa-tgl-lahir').value,
                alamat: document.getElementById('dewasa-alamat').value,
                jenis_kelamin: document.getElementById('dewasa-jk').value,
                pekerjaan: document.getElementById('dewasa-pekerjaan').value,
                no_hp: document.getElementById('dewasa-no-hp').value,
                level: document.getElementById('dewasa-level').value,
                program: programs,
                program_tipe: 'dewasa'
            };
            
            data.dewasa.push(peserta);
            pendaftaranSuccess.classList.add('show');
            dewasaForm.reset();
            setTimeout(() => pendaftaranSuccess.classList.remove('show'), 4000);
        });

        // Absensi Tab Switching
        tabBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                tabBtns.forEach(b => b.classList.remove('active'));
                tabContents.forEach(c => c.style.display = 'none');
                
                btn.classList.add('active');
                document.getElementById('tab-' + btn.dataset.tab).style.display = 'block';
                
                if (btn.dataset.tab === 'daftar') {
                    renderDaftarSantri();
                }
            });
        });

        // Bulan and Pekan selection for Absensi
        bulanFilter.addEventListener('change', () => {
            state.bulanAktif = bulanFilter.value;
            renderAbsensiTable();
        });

        pekanFilter.addEventListener('change', () => {
            state.pekanAktif = pekanFilter.value;
            renderAbsensiTable();
        });

        // Absensi Functions
        function hitungPersentase(statusArray) {
            // Hadir, izin, dan sakit dihitung sebagai hadir
            const hadirCount = statusArray.filter(s => s === 'hadir' || s === 'izin' || s === 'sakit').length;
            const totalHari = statusArray.length;
            return Math.round((hadirCount / totalHari) * 100);
        }

        function getKelasPersentase(persentase) {
            if (persentase >= 80) return 'persentase-hadir';
            if (persentase >= 60) return 'persentase-cukup';
            return 'persentase-rendah';
        }

        function createAbsenRow(index) {
            const row = document.createElement('tr');
            row.dataset.index = index;
            
            row.innerHTML = `
                <td>${index + 1}</td>
                <td><input type="text" class="nama-santri" placeholder="Nama santri..." style="width: 100%; padding: 10px; border-radius: 8px; border: 2px solid #cbd5e0;"></td>
                <td><select class="absen-select"><option value="">Pilih</option><option value="hadir">Hadir</option><option value="izin">Izin</option><option value="sakit">Sakit</option><option value="alfa">Alfa</option></select></td>
                <td><select class="absen-select"><option value="">Pilih</option><option value="hadir">Hadir</option><option value="izin">Izin</option><option value="sakit">Sakit</option><option value="alfa">Alfa</option></select></td>
                <td><select class="absen-select"><option value="">Pilih</option><option value="hadir">Hadir</option><option value="izin">Izin</option><option value="sakit">Sakit</option><option value="alfa">Alfa</option></select></td>
                <td><select class="absen-select"><option value="">Pilih</option><option value="hadir">Hadir</option><option value="izin">Izin</option><option value="sakit">Sakit</option><option value="alfa">Alfa</option></select></td>
                <td><select class="absen-select"><option value="">Pilih</option><option value="hadir">Hadir</option><option value="izin">Izin</option><option value="sakit">Sakit</option><option value="alfa">Alfa</option></select></td>
                <td class="persentase-cell">0%</td>
                <td><button class="hapus-baris"><i class="fas fa-trash"></i></button></td>
            `;
            
            // Add event listeners for status coloring and percentage calculation
            const selects = row.querySelectorAll('.absen-select');
            selects.forEach(select => {
                select.addEventListener('change', function() {
                    // Reset classes
                    this.className = 'absen-select';
                    
                    // Add color class
                    if (this.value === 'hadir') this.classList.add('absen-hadir');
                    else if (this.value === 'izin') this.classList.add('absen-izin');
                    else if (this.value === 'sakit') this.classList.add('absen-sakit');
                    else if (this.value === 'alfa') this.classList.add('absen-alfa');
                    
                    // Recalculate percentage
                    const statusArray = Array.from(selects).map(s => s.value);
                    const persentase = hitungPersentase(statusArray);
                    const persentaseCell = row.querySelector('.persentase-cell');
                    persentaseCell.textContent = persentase + '%';
                    persentaseCell.className = 'persentase-cell ' + getKelasPersentase(persentase);
                });
            });
            
            // Add delete button listener
            row.querySelector('.hapus-baris').addEventListener('click', () => {
                row.remove();
                renumberRows();
            });
            
            return row;
        }

        function renumberRows() {
            const rows = absenBody.querySelectorAll('tr');
            rows.forEach((row, index) => {
                row.querySelector('td:first-child').textContent = index + 1;
            });
        }

        tambahBarisBtn.addEventListener('click', () => {
            const index = absenBody.children.length;
            const row = createAbsenRow(index);
            absenBody.appendChild(row);
        });

        simpanAbsenBtn.addEventListener('click', () => {
            const rows = absenBody.querySelectorAll('tr');
            if (rows.length === 0) {
                alert('Belum ada data absensi yang dimasukkan.');
                return;
            }
            
            let valid = true;
            let data = [];
            
            rows.forEach(row => {
                const nama = row.querySelector('.nama-santri').value.trim();
                const status = Array.from(row.querySelectorAll('.absen-select')).map(s => s.value);
                
                if (!nama) {
                    valid = false;
                    row.querySelector('.nama-santri').style.borderColor = 'var(--merah)';
                } else {
                    row.querySelector('.nama-santri').style.borderColor = '#cbd5e0';
                }
                
                if (status.some(s => s === '')) {
                    valid = false;
                    row.querySelectorAll('.absen-select').forEach(s => {
                        if (s.value === '') s.style.borderColor = 'var(--merah)';
                    });
                } else {
                    row.querySelectorAll('.absen-select').forEach(s => s.style.borderColor = '#cbd5e0');
                }
                
                if (valid || (nama && !status.some(s => s === ''))) {
                    data.push({ 
                        nama, 
                        status,
                        persentase: hitungPersentase(status)
                    });
                }
            });
            
            if (!valid) {
                alert('Mohon lengkapi semua kolom yang belum diisi.');
                return;
            }
            
            alert(`Absensi berhasil disimpan!\nJumlah santri: ${data.length}\nRata-rata kehadiran: ${data.reduce((acc, d) => acc + d.persentase, 0) / data.length | 0}%`);
            // Here you would typically send data to server
        });

        // Render absensi table
        function renderAbsensiTable() {
            absenBody.innerHTML = '';
            const row = createAbsenRow(0);
            absenBody.appendChild(row);
        }

        // Render daftar santri untuk tab absensi
        function renderDaftarSantri() {
            daftarSantriBody.innerHTML = '';
            
            let semuaSantri = [];
            
            // Gabungkan semua data santri
            data.tpq.forEach(s => {
                semuaSantri.push({
                    ...s,
                    program: 'TPQ',
                    levelText: getLevelText(s.level, 'tpq')
                });
            });
            
            data.dewasa.forEach(s => {
                semuaSantri.push({
                    ...s,
                    nama: s.nama,
                    tgl_lahir: s.tgl_lahir,
                    alamat: s.alamat,
                    level: s.level,
                    program: 'Dewasa',
                    levelText: getLevelText(s.level, 'dewasa')
                });
            });
            
            // Tambahkan data dummy jika belum ada
            if (semuaSantri.length === 0) {
                const dummyData = [
                    { nama: "Ahmad Fauzi", tgl_lahir: "2015-05-12", alamat: "Jl. Sudirman No. 45, Bandung", level: "2", program: "TPQ", levelText: "Level 2 (Menengah)" },
                    { nama: "Siti Aisyah", tgl_lahir: "2016-08-23", alamat: "Jl. Diponegoro No. 78, Bandung", level: "1", program: "TPQ", levelText: "Level 1 (Pemula)" },
                    { nama: "Muhammad Rizal", tgl_lahir: "1990-03-17", alamat: "Jl. Merdeka No. 12, Bandung", level: "3", program: "Dewasa", levelText: "Level 3 (Lanjut)" },
                    { nama: "Dewi Lestari", tgl_lahir: "1988-11-05", alamat: "Jl. Antapani No. 34, Bandung", level: "2", program: "Dewasa", levelText: "Level 2 (Menengah)" }
                ];
                semuaSantri = dummyData;
            }
            
            semuaSantri.forEach((santri, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${santri.nama}</td>
                    <td>${formatTanggal(santri.tgl_lahir)}</td>
                    <td>${santri.alamat}</td>
                    <td><span class="level-badge level-${santri.level}">${santri.levelText}</span></td>
                    <td>${santri.program}</td>
                `;
                daftarSantriBody.appendChild(row);
            });
        }

        // Render data santri untuk halaman data santri
        function renderDataSantri() {
            dataSantriBody.innerHTML = '';
            
            let semuaSantri = [];
            
            // Gabungkan semua data santri
            data.tpq.forEach(s => {
                semuaSantri.push({
                    ...s,
                    tipe: 'tpq',
                    program: 'TPQ',
                    levelText: getLevelText(s.level, 'tpq')
                });
            });
            
            data.dewasa.forEach(s => {
                semuaSantri.push({
                    ...s,
                    tipe: 'dewasa',
                    nama: s.nama,
                    tgl_lahir: s.tgl_lahir,
                    alamat: s.alamat,
                    level: s.level,
                    program: 'Dewasa',
                    levelText: getLevelText(s.level, 'dewasa')
                });
            });
            
            // Tambahkan data dummy jika belum ada
            if (semuaSantri.length === 0) {
                const dummyData = [
                    { nama: "Ahmad Fauzi", tgl_lahir: "2015-05-12", alamat: "Jl. Sudirman No. 45, Bandung", level: "2", program: "TPQ", levelText: "Level 2 (Menengah)", tipe: 'tpq' },
                    { nama: "Siti Aisyah", tgl_lahir: "2016-08-23", alamat: "Jl. Diponegoro No. 78, Bandung", level: "1", program: "TPQ", levelText: "Level 1 (Pemula)", tipe: 'tpq' },
                    { nama: "Muhammad Rizal", tgl_lahir: "1990-03-17", alamat: "Jl. Merdeka No. 12, Bandung", level: "3", program: "Dewasa", levelText: "Level 3 (Lanjut)", tipe: 'dewasa' },
                    { nama: "Dewi Lestari", tgl_lahir: "1988-11-05", alamat: "Jl. Antapani No. 34, Bandung", level: "2", program: "Dewasa", levelText: "Level 2 (Menengah)", tipe: 'dewasa' }
                ];
                semuaSantri = dummyData;
            }
            
            // Filter berdasarkan program dan level
            const filterProgram = document.getElementById('filter-program').value;
            const filterLevel = document.getElementById('filter-level').value;
            
            let filteredSantri = semuaSantri;
            
            if (filterProgram !== '') {
                filteredSantri = filteredSantri.filter(s => s.program.toLowerCase().includes(filterProgram));
            }
            
            if (filterLevel !== '') {
                filteredSantri = filteredSantri.filter(s => s.level === filterLevel);
            }
            
            filteredSantri.forEach((santri, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${santri.nama}</td>
                    <td>${formatTanggal(santri.tgl_lahir)}</td>
                    <td>${santri.alamat}</td>
                    <td><span class="level-badge level-${santri.level}">${santri.levelText}</span></td>
                    <td>${santri.program}</td>
                `;
                dataSantriBody.appendChild(row);
            });
        }

        // Helper functions
        function getLevelText(level, tipe) {
            if (tipe === 'tpq') {
                const levels = {
                    '1': 'Level 1 (Pemula)',
                    '2': 'Level 2 (Menengah)',
                    '3': 'Level 3 (Lanjut)',
                    '4': 'Level 4 (Tahfiz)'
                };
                return levels[level] || 'Level Tidak Diketahui';
            } else {
                const levels = {
                    '1': 'Level 1 (Pemula - Iqro\')',
                    '2': 'Level 2 (Menengah - Juz 30)',
                    '3': 'Level 3 (Lanjut - Juz 1-10)',
                    '4': 'Level 4 (Tahfiz - Juz 11-30)'
                };
                return levels[level] || 'Level Tidak Diketahui';
            }
        }

        function formatTanggal(tgl) {
            if (!tgl) return '-';
            const date = new Date(tgl);
            return date.toLocaleDateString('id-ID', {
                day: 'numeric',
                month: 'long',
                year: 'numeric'
            });
        }

        // Initialize
        tampilkanHalaman('utama');
        
        // Add event listener for filter changes in data santri page
        document.getElementById('filter-program').addEventListener('change', renderDataSantri);
        document.getElementById('filter-level').addEventListener('change', renderDataSantri);
    </script>
</body>
</html>

