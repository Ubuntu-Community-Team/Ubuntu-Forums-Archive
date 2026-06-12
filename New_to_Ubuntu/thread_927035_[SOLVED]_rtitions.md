---
title: "[SOLVED] rtitions"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-22
I'm reading the system administrator's guide (cause that's how I roll) and I'm in the chapter about partitions, following directions but alas it does not work see?

adamogardner@CRONUS:~$ fdisk -l /dev/hda
adamogardner@CRONUS:~$ fdisk -l /dev/hda3
adamogardner@CRONUS:~$ fdisk -l
adamogardner@CRONUS:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
adamogardner@CRONUS:~$ fdisk /dev/hda

Unable to open /dev/hda
adamogardner@CRONUS:~$ fdisk /dev/hda3

Unable to open /dev/hda3
adamogardner@CRONUS:~$ fdisk /dev/hda1

Unable to open /dev/hda1
adamogardner@CRONUS:~$ fdisk /dev/hda2

Unable to open /dev/hda2
adamogardner@CRONUS:~$ fdisk /dev/hda4

Unable to open /dev/hda4

edit: something happened to my original heading, "what's wrong with my fdisk commands?"

---

### Post by hyper_ch on 2008-09-22
```

sudo fdisk -l

```

---

### Post by Mornedhel on 2008-09-22
You need administration rights. Use sudo fdisk -l /dev/hda3.

---

### Post by adamogardner on 2008-09-22
duh

---

### Post by hyper_ch on 2008-09-22
well, we all learn ;) hasn't been a long time ago when I had the same problem ;)

---

