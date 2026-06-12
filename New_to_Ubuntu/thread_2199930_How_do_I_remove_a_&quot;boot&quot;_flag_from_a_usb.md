---
title: "How do I remove a &quot;boot&quot; flag from a usb stick?"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-16
How do I do it? I believe the usb stick wil not let me format it while it has a "boot" flag. I am new to Ubuntu, again; I was on the forums 4-5 years ago, and I have forgotten everything.:confused:

---

### Post by tfrue on 2014-01-16
We would use *fdisk*. Fdisk is a partitioning tool for MBR partitions, like USB. Type:
```
sudo fdisk -l ( To get the /dev/sdxx of your USB)
sudo fdisk /dev/sdb (Assuming the USB is /dev/sdb)
a (Toggle boot flag)
w (To write the changes)

```

You can also use fdisk to create a new msdos (MBR) on the usb.
```

sudo fdisk /dev/sdb
o
enter
n
p
1
enter
enter
enter
p (To make sure the new partition is showing)
t (To change the type)
7 (NTFS)
or
b (Which should do FAT32)
w 
```

Good luck,
Chris

---

