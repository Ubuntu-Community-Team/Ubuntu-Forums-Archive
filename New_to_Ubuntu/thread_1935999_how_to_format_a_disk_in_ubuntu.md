---
title: "how to format a disk in ubuntu"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by maheshtatva on 2012-03-05
i was shocked to know that my usb disk got attacked by virus from a windows 7 user 
still my pc works well(ubuntu rocks) i would like to format my usb disk as im new to linux

---

### Post by seawolf167 on 2012-03-05
You can use GParted which should be installed by default.

Hit [ALT][F2] type in GParted and hit enter to open it up.

If for some reason it is not installed, you can install it with

```
sudo apt-get install gparted
```If you format it FAT, NTFS then Windows will be able to read it. Note that NTFS is a journaling file system so FAT is recommended unless you know you'll need support for files larger than 4GB.

I'm assuming you mean a USB flash drive not external hard drive. If it is an external hard drive, use NTFS if Windows needs to read/write it, else use ext4.

---

### Post by Frogs Hair on 2012-03-05
Gparted is not installed by default . It has not been included on my last two clean installations .

---

### Post by seawolf167 on 2012-03-05
> **Frogs Hair said:**
> Gparted is not installed by default . It has not been included on my last two clean installations .

Good to know! Did they replace it with anything or just remove it from the standard installation?

---

### Post by maheshtatva on 2012-03-05
this what i found installing  Gparted
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by seawolf167 on 2012-03-05
You can only have one package manager open - is Synaptic open? The Ubuntu Software Center? Close those, then do they command line install, or alternatively, just search and install gparted through the software center.

---

### Post by ubudog on 2012-03-05
> **maheshtatva said:**
> this what i found installing  Gparted
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Do you have synaptic or another apt-get running?

---

### Post by ajgreeny on 2012-03-05
> **seawolf167 said:**
> Good to know! Did they replace it with anything or just remove it from the standard installation?
It has never been in a default installation, though it is always on the live CD/DVD, so you can use that if you don't want to install it on your OS.

---

### Post by maheshtatva on 2012-03-05
thanks everyone for advise i would like to know more about Gparted partitioning software. from google i got to know that gparted live cd can be used for partitioning the drive, your feedback will be very kind

---

### Post by seawolf167 on 2012-03-05
What specifically do you want to know?

[GParted wiki]("http://en.wikipedia.org/wiki/GParted")
[GParted home page]("http://gparted.sourceforge.net/")
[Disk partitioning wiki]("http://en.wikipedia.org/wiki/Disk_partitioning")
[Ubuntu how-to-partition]("https://help.ubuntu.com/community/HowtoPartition")
[Ubuntu partition sizes]("https://help.ubuntu.com/8.04/installation-guide/i386/partition-sizing.html")
[Partitioning basics]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")

---

### Post by maheshtatva on 2012-03-06
partition basic...

---

### Post by seawolf167 on 2012-03-06
[Partitioning basics ]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics")link reposted.

---

### Post by maheshtatva on 2012-03-06
partition basic

---

