---
title: "Why NTFS is so faster than ext4 for me?"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by Daniyal_Javani on 2015-10-29
I check this with copy a 1GB file from NTFS and ext4 (root or /) partition (in same) HDD to RAM (/run/shm), but  NTFS was 3 times faster than ext4. Could you please tell me why?

---

### Post by mastablasta on 2015-10-29
same hard disk drive? on the same part of hard disk? ext4 wasn't at the end and NTFS on beginning of the drive?

EXT is a more advanced system and has more features than NTFS, so this could also be causing some slow down.

---

### Post by Daniyal_Javani on 2015-10-29
> **arminmohring said:**
> 
hdd or ssd?


hdd

> **mastablasta said:**
> same hard disk drive? on the same part of hard disk? ext4 wasn't at the end and NTFS on beginning of the drive?

Yes, same HDD, ext4 was on beginning of the drive.

Any way to fix this issue?

---

### Post by mastablasta on 2015-10-29
perhaps you are not testing it properly or some data is deceiving you.

ext4 should probably be a bit faster. here are some phoronix tests on kernel 4.0: [http://www.phoronix.com/scan.php?page=article&item=linux-40-hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-40-hdd&num=1)

---

