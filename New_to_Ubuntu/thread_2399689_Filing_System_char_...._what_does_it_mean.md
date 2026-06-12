---
title: "Filing System char ../../ what does it mean"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by robertzito on 2018-08-28
I am new to Ubuntu and I am trying to format and perform a fresh install, but the disk does not erase everything when I look at the properties of the devices in dev the drives are "X" ed out and properties on /dev/disk/by-uuid I am seeing linked to block device with target ../../nvme0n1p3 what is ../../ owned by because root cant get rid of them and I can not do a fresh install.

---

### Post by monkeybrain20122 on 2018-08-28
../ means one level up from current directory, ../../ two levels etc.

---

### Post by Impavidus on 2018-08-29
I may not fully understand the question, but /dev, /sys and /proc are so-called pseudofilesystems. The contents of those aren't present on your drive, they may be your drive.

---

### Post by The Cog on 2018-08-29
Impavidus is right. /dev, /sys and /proc are not real directories on disk. They are directories and files inside the OS's imagination, created to provide access to devices that the device drivers find, and to information on the kernel settings and the state of currently running processes. Everything in /dev is created by device drivers and /dev/nvme0n1p3 is almost certainly a representation of your hard disk. If you were to write to that, you would end up writing raw data to the disk itself (and this is how you would erase the partition table of you wanted to).

---

