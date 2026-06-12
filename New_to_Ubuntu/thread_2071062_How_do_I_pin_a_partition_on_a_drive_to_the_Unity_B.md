---
title: "How do I pin a partition on a drive to the Unity Bar."
date: 2012-10-14
forum: New to Ubuntu
---

### Post by tommytiptree on 2012-10-14
Hi, I have two disk drives in my PC with Ubuntu 12.04 loaded on one drive and I use the other drive with separate partitions to store my music and photos. To access either my photos or music I have to go to the home folder and select which partition I wish to open. Although I pin the partition to the unity bar it is never there when I restart my PC. Is there any way that I can launch my music and photo partitions from the unity bar, thanks.

---

### Post by newb85 on 2012-10-14
It sounds like your partition for music and photos isn't set up to automatically mount at startup.  (Nautilus will show partitions in the sidebar that aren't mounted, and when you click them, it mounts them.)  Your fstab file (**f**ile **s**ystem **tab**le) lists the partitions that are automatically mounted.

Please see the following from the official documentation:

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by tommytiptree on 2012-10-14
Many thanks for your help, tried this and it works.

---

