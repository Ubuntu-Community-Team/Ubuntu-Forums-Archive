---
title: "How to make a partion after making entire hard disk into primary drive?"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by ramaprakashak on 2014-02-02
I did a foolish job of erasing whole disk and installing Ubuntu on it, while I wanted Window 8 along with it. Now not able to create a partiton since the one and only partion is always mounted with OS running on it. Help Me

---

### Post by oldfred on 2014-02-02
You have to use a live Installer DVD or flash drive. You cannot use gparted from a working system.
Is your system BIOS(MBR) or UEFI(gpt)?

       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)


 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by ramaprakashak on 2014-02-02
It is a BIOS MBR. Now going to use USB installer I think that is going to solve the problem. Thank you.

---

