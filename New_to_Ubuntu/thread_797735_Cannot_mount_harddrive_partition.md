---
title: "Cannot mount harddrive partition"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by - 000 - on 2008-05-17
I have a partition on my harddrive, and right now it contains some music.  All of a sudden, when I restarted my computer, the partition is no longer mounted and when I click on the volume it says "cannot mount volume:Invalid mount option when attempting to mount the volume.".

I tried sudo mount /dev/sda5 /media (which was what it was before), and it does nothing.

---

### Post by - 000 - on 2008-05-17
hello?

---

### Post by herbster on 2008-05-17
Paste the output of

```
cat /etc/fstab
```

and

```
sudo fdisk -l
```

---

### Post by shadow-of-sin on 2008-05-17
What is the filesystem on the partition? Please, type the following command in the terminal and post your results:
```
sudo fdisk -l
```

---

### Post by - 000 - on 2008-05-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8a2f9c0b-7068-48af-ab2f-8274b6114a67 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0da0f598

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8455    67914756    5  Extended
/dev/sda2            8456        9729    10233405   83  Linux
/dev/sda5               1        8455    67914724+  83  Linux

---

### Post by shadow-of-sin on 2008-05-17
First of all, create a mount point, e.g:
```
sudo mkdir /media/drive
```

Now add the following line to your /etc/fstab file:
```
/dev/sda5 /media/disk ext3 defaults 0 0
```

Then type the following command in the terminal:
```
sudo mount -a
```

Your drive should be mounted now.

---

### Post by - 000 - on 2008-05-17
I don't know how to add a file to fstab

---

### Post by - 000 - on 2008-05-17
bump

---

### Post by herbster on 2008-05-17
You have to add the line to your /etc/fstab file. Open it like this:

```
sudo gedit /etc/fstab
```

and on a **new** line add that line. Then save and close the file, issue the command shadow-of-sin gave (sudo mount -a).

---

### Post by - 000 - on 2008-05-17
Thank you, it works now :)

---

