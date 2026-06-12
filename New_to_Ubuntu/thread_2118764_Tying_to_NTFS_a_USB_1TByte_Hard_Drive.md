---
title: "Tying to NTFS a USB 1TByte Hard Drive"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by happyhacker on 2013-02-22
I am using gparted and when I try to reformat using default fields it ends up with an error: "mkntfs -Q -v -L "" dev/sdb2" - Device is too small 1023 KiB. Minimum NTFS size is 1 KiB."

Advice appreciated.

PS this drive was removed from a windows PC and was reported as faulty and I am trying to restore it if possible.

UPDATE: I have refreshed gparted and it now shows a 931.51GB partition ntfs and a small unallocated bit of 1.17 of MiB! Is this now correct or how can I put that into the main partition?

---

### Post by thermion on 2013-02-22
It's fine the way it is right now. You allways end up with some space being unallocated.

---

### Post by jmore9 on 2013-02-22
Thats about right for 1tb drives.  The bigger you get the larger the overhead the drive uses.  All three of my usb 1tbs use about that much for over head

---

### Post by happyhacker on 2013-02-22
Thanks, I've connected now to windows 7 and had to assign a drive letter and now it appears as a USB drive.

---

