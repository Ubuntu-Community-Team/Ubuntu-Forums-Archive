---
title: "[SOLVED] How to recognise your external hard drive"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by sprogmeister on 2008-08-21
Apologies first for my newness and lack of knowledge. I was reading through the thread "***Wipe Clean External Hard Drive***" an dfound I cannot work out which drive is my usb hard drive. It scares me to think I may wipe the wrong hdd. Can anyone help please?

---

### Post by Het Irv on 2008-08-21
Are your external drive and internal drive the same size?

Please post the output of ```
sudo fdisk -l
```

---

### Post by taqkavar on 2008-08-21
```
sudo fdisk -l
```
will show all your hard drives, their partitions and their respective sizes. You can tell the hard drives apart from their sizes or number of partitions. If you don't know how large are your hard drives, then just disconnect the usb one and see which one disappears from the output of fdisk -l

---

### Post by sprogmeister on 2008-08-24
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf363f363

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18244   146544898+   7  HPFS/NTFS
/dev/sda2           18245       30401    97651102+   5  Extended
/dev/sda5           18245       30024    94622818+  83  Linux
/dev/sda6           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f580c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         912     7325608+  12  Compaq diagnostics
/dev/sdb2   *         913        5776    39070080    7  HPFS/NTFS
/dev/sdb3            5777        9729    31752472+   5  Extended
/dev/sdb5            5777        5898      979933+  82  Linux swap / Solaris
/dev/sdb6            5899        9729    30772476   83  Linux

---

