---
title: "I can't boot up from my external hard drive"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by openation1 on 2013-12-31
Hello everyone ............ I try to open my external usb hard drive but I can't.... I try to boot up from it and it says that theres no bootable disk..... i have 12.04 on my disk I used to open it up but I cant no more..... i change the settings from cmos but still cant boot . please help me... thank you

openation@OptiPlex-GX520:~$  sudo fdisk -lu
[sudo] password for openation: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a715

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   151549951    75773952   83  Linux
/dev/sda2       151551998   156248063     2348033    5  Extended
/dev/sda5       151552000   156248063     2348032   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f8a5

   Device Boot      Start         End      Blocks   Id  System
openation@OptiPlex-GX520:~$

---

### Post by sandyd on 2013-12-31
> **openation1 said:**
> Hello everyone ............ I try to open my external usb hard drive but I can't.... I try to boot up from it and it says that theres no bootable disk..... i have 12.04 on my disk I used to open it up but I cant no more..... i change the settings from cmos but still cant boot . please help me... thank you

openation@OptiPlex-GX520:~$  sudo fdisk -lu
[sudo] password for openation: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a715

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   151549951    75773952   83  Linux
/dev/sda2       151551998   156248063     2348033    5  Extended
/dev/sda5       151552000   156248063     2348032   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f8a5

   Device Boot      Start         End      Blocks   Id  System
openation@OptiPlex-GX520:~$
The above output shows that there are no partitions on your external disk (assuming it is /dev/sdb)

---

### Post by openation1 on 2013-12-31
hello happy new year to all of you........... how can I open my external hard drive i have a lot of documents and videos that i dont wanna loose. please help me thank you

---

### Post by Mark Phelps on 2014-01-01
If your external drive is "sdb", as the Moderator already said, there are NO partitions on that drive, so there is no way to mount it routinely to recover the files.

If it was formatted using a Linux filesystem, you can check out using TestDisk to try to recover the files.

If it was formatted using a Windows filesystem, you would do better using Windows data recovery apps.

We need to know how it was formatted to provide any more details.

---

