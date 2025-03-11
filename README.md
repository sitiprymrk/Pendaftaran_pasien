<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulir Pendaftaran Pasien Rawat Jalan</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; background: #f4f4f4; }
        .container { width: 80%; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px gray; }
        h2 { text-align: center; }
        label { font-weight: bold; }
        input, select { width: 100%; padding: 8px; margin: 5px 0; border-radius: 5px; border: 1px solid #ccc; }
        button { background: #007bff; color: white; padding: 10px; border: none; border-radius: 5px; cursor: pointer; }
        .dashboard { display: flex; justify-content: space-between; margin-top: 20px; }
        .dashboard div { width: 30%; padding: 15px; background: #fff; box-shadow: 0 0 10px gray; border-radius: 10px; }
    </style>
</head>
<body>
    <div class="container">
        <h2>FORMULIR PENDAFTARAN PASIEN RAWAT JALAN</h2>
        <form id="formPendaftaran">
            <label>Nama Pasien:</label>
            <input type="text" id="nama" required>
            
            <label>Nomor Rekam Medis:</label>
            <input type="text" id="nomor_rm" required>
            
            <label>NIK:</label>
            <input type="text" id="nik" required>
            
            <label>Nomor Telepon:</label>
            <input type="text" id="telepon" required>
            
            <label>Pekerjaan:</label>
            <input type="text" id="pekerjaan" required>
            
            <label>Pendidikan:</label>
            <input type="text" id="pendidikan" required>
            
            <label>Alamat:</label>
            <input type="text" id="alamat" required>
            
            <label>Status Pembayaran:</label>
            <select id="status_pembayaran">
                <option value="BPJS">BPJS</option>
                <option value="Asuransi">Asuransi</option>
                <option value="Umum">Umum</option>
            </select>
            
            <label>Tujuan Poliklinik:</label>
            <input type="text" id="poli" required>
            
            <label>Tanggal dan Waktu Pendaftaran:</label>
            <input type="datetime-local" id="tanggal" required>
            
            <button type="submit">Daftar</button>
        </form>
    </div>

    <div class="dashboard">
        <div id="antrian">
            <h3>Nomor Antrian</h3>
            <p id="nomorAntrian">-</p>
        </div>
        <div id="statistik">
            <h3>Statistik Pembayaran</h3>
            <p>BPJS: <span id="bpjs">0</span></p>
            <p>Asuransi: <span id="asuransi">0</span></p>
            <p>Umum: <span id="umum">0</span></p>
        </div>
    </div>

    <script>
        let antrian = 0;
        let bpjsCount = 0, asuransiCount = 0, umumCount = 0;

        document.getElementById("formPendaftaran").addEventListener("submit", function(event) {
            event.preventDefault();
            antrian++;
            document.getElementById("nomorAntrian").innerText = antrian;
            
            let status = document.getElementById("status_pembayaran").value;
            if (status === "BPJS") bpjsCount++;
            else if (status === "Asuransi") asuransiCount++;
            else if (status === "Umum") umumCount++;
            
            document.getElementById("bpjs").innerText = bpjsCount;
            document.getElementById("asuransi").innerText = asuransiCount;
            document.getElementById("umum").innerText = umumCount;
            
            alert("Pendaftaran Berhasil!");
            document.getElementById("formPendaftaran").reset();
        });
    </script>
</body>
</html>