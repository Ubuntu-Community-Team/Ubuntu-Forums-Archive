---
title: "Dmesg message -what does it mean?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by deri on 2013-06-06
2906.361159] JFS: nTxBlock = 8192, nTxLock = 65536
[ 2906.418639] NTFS driver 2.1.30 [Flags: R/O MODULE].
[ 2906.500199] QNX4 filesystem 0.2.3 registered.
[ 2906.549361] xor: measuring software checksum speed
[ 2906.588850]    prefetch64-sse:  3131.000 MB/sec
[ 2906.628912]    generic_sse:  3027.000 MB/sec
[ 2906.628918] xor: using function: prefetch64-sse (3131.000 MB/sec)
[ 2906.721079] raid6: sse2x1    1206 MB/s
[ 2906.789209] raid6: sse2x2    2034 MB/s
[ 2906.857282] raid6: sse2x4    2337 MB/s
[ 2906.857287] raid6: using algorithm sse2x4 (2337 MB/s)
[ 2906.857292] raid6: using intx1 recovery algorithm
[ 2906.913848] Btrfs loaded


I don't have Btrfs partitions or raid on my computer...

---

### Post by dino99 on 2013-06-06
maybe the dmraid package is installed; in such a case, remove it (set a fake raid)

---

### Post by deri on 2013-06-07
According to moun update manager it's not installed.

---

