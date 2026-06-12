---
title: "using Ubuntu to ?partition? an external hard drive"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by leej51503 on 2011-12-03
I am interested in partitioning my 1TB hard drive in order to reinstall the recovery disks for Windows 7 Home Premium that came with the system prior to wiping/installing Ubuntu 11.10.  I found and installed GParted Partition Editor in hopes this would help.  I am  VERY inexperienced, and would need someone with a lot of patience to help me through this without much knowledge on my end.  Thanks in advance.
[EMAIL="leej51503@gmail.com"]
[/EMAIL]

---

### Post by oldfred on 2011-12-03
Welcome to the forums.

I removed your email as this forum is regularly scanned & you would get tons of spam. Use PM once you have enough posts (I think).

You cannot install Windows to an external drive unless Windows sees it a an internal. USB connection definitely will not work. Not sure about e-SATA type connections. Windows build in checks and it designed to only work with one system. I put a new motherboard in my XP system and it had to call home  to verify it was the same system.

---

### Post by oldfred on 2011-12-05
I use gparted all the time. Sometimes from my Ubuntu disk, but I also download the gparted liveCD just to have another boot disk. I now put them all on a USB flash drive as I used to download several repairCDs for every new install as alternatives.

Anytime you change partitions around, be sure to have good backups. Any powerfailure, cat/dog/kid disconnecting wires or user error can lead to major issues if you do not have backups.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Note that grub2 had/has a bug with very large / (root) partitions. It is best to keep a smaller / partition and use separate /home and/or /data partitions. My 2year old  640GB drive still is not fully allocated. I used one or two primary partitions and put all the rest into a extended partition. I now add extended partitions as needed, but most are just new / to test/try another Linux or new Ubuntu.

---

### Post by leej51503 on 2011-12-05
I have updated this thread, because I am now trying to use the INTERNAL hard drive already installed.

---

### Post by oldfred on 2011-12-05
Do you have the recovery disks or a backup of Windows. The recovery often just installs to the entire drive, not sure if it will work on your much larger drive or not. But either way you then should be able to repartition.

I would make Windows the first partition. Sometimes repairs/installs do not work unless it sees a NTFS primary partition with the boot flag. You can set boot flag with gparted. Primary partitions are sda1 thru sda4. An extended partition counts as one of the primaries and you can only have one extended partition. You can make as many logical partitions as you want inside the extended. So I usually make a couple of primaries at the beginning of the drive, and then make the entire rest of the drive the extended partition even if I do not immediately create logical partitions for all of the extended. I just save some unallocated space for future use.

---

