## Tugas 1: Konektivitas Dasar

**Tanggal**: 22/11/2025
**Nama**: Muzhaffar Ammar
**Status K3s**: WORKING

### Github Repo:
https://github.com/theammars/open5gs-exp-with_kubernetes.git

### gNB Registration
- Status: SUCCESS
- Time taken: 41 ms
- AMF Connection: ESTABLISHED

### UE Registration
- Status: SUCCESS
- Time taken: 430 ms
- IMSI: 001011000000001
- TUN Interface: uesimtun0
- IP Address: 10.45.0.3

### Connectivity Tests
| Test | Result | RTT (ms) |
|------|--------|----------|
| UPF Gateway (10.45.0.1) | ✓ PASS | 9.47 |
| Internet (8.8.8.8) | ✓ PASS | 42.04 |
| DNS Resolution | ✓ PASS | - |
| HTTP/HTTPS | ✓ PASS | - |

### Issues Encountered
- MongoDB Crash (Illegal Instruction) pada deployment otomatis
- UE gagal connect dengan error FIVEG_SERVICES_NOT_ALLOWED

### Resolution
- Menghapus MongoDB bawaan script dan menjalankan MongoDB versi 4.4 secara manual di dalam Pod Kubernetes karena CPU VirtualBox tidak mendukung AVX (untuk versi 5.0+).
- Menyesuaikan konfigurasi PLMN ID di AMF menjadi 001/01 agar sesuai dengan UE. Mengubah data di Database MongoDB dengan set access_restriction_data: 0 (Allow All). Melakukan Restart Pod AMF dan UDM untuk membersihkan cache data lama.

### Screenshoot
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/getnodes.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/getpods.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/getsvc.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/gnbregis.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/ueregis.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/addrshow.png?raw=true  
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/pinguesimtun0_10.45.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/pinguesimtun0_10.45.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/nslookup%20goggle.png?raw=true
https://github.com/theammars/open5gs-exp-with_kubernetes/blob/main/Documentation/curluesimtun0google.png?raw=true