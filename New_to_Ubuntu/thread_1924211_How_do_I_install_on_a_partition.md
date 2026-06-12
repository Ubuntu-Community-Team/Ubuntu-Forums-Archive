---
title: "How do I install on a partition?"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by Vikezor on 2012-02-12
I created a partition to install Ubuntu on, but it doesn't show up in the installer. :( I created the partition in Disk Manager in Windows.

---

### Post by benpack101 on 2012-02-12
I always use gparted to created different partitions before installing Ubuntu (and it has always worked). What format is this partition that you just created?

---

### Post by Vikezor on 2012-02-12
Simple partition.

---

### Post by benpack101 on 2012-02-12
A Simple partition? That isn't a format type,

first of all I would make sure to have everything backed up.
I would then boot off of the Ubuntu CD/USB and run gparted. 
Go ahead and follow the directions and such off of this page [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Don't forget to create a linux swap space.

Depending on the Ubuntu version you are using, you may need to : sudo apt-get install gparted

---

### Post by Mark Phelps on 2012-02-12
> **Vikezor said:**
> I created a partition to install Ubuntu on, but it doesn't show up in the installer. :( I created the partition in Disk Manager in Windows.

Windows only creates partitions that use Windows filesystems.

Ubuntu is Linux, not Windows -- it needs a partition using a Linux filesystem.

As mentioned, you will need to boot from an Ubuntu CD and use GParted to create the Linux filesystem partition.

---

### Post by centaurusa on 2012-02-12
> **Vikezor said:**
> I created a partition to install Ubuntu on, but it doesn't show up in the installer. :( I created the partition in Disk Manager in Windows.

Run GParted from the live-CD installation disk.  This will show Windows partitions as something like Partition = /dev/sda3, File System = ntfs, Size = 71.12 GB.  You should be able to determine which is the partition that you created.  What you need to do is to delete this (presumably empty) partition to make it "unallocated" space.  Then, you can create  root and swap partitions during your Ubuntu installation by using the manual partitioner (probably called the "Something Else" option).  See:  [http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/)

---

### Post by arpanaut on 2012-02-12
This thread should help you; posts 5,6 & 9 will be most helpful.
[http://ubuntuforums.org/showthread.php?t=1910623](http://ubuntuforums.org/showthread.php?t=1910623)

Simple partitions are a MS proprietary scheme that Linux can't use.

Good Luck

---

### Post by d4m1r on 2012-02-12
1) Burn a Ubuntu install from an .iso or extract the files to a USB
2) Create a partition for Ubuntu before installing Ubuntu using the previously mentioned CD or USB

---

