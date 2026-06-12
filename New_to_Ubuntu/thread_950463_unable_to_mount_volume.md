---
title: "unable to mount volume"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by khael14 on 2008-10-17
please help me im a new user of ubuntu and i really dont know how to use it.
when im opening the hard drive a message flashed and it reads " unable to mount volume"
ntfs signature is missing...
i dont know what to do!

---

### Post by Ryadt on 2008-10-17
Can you post the exact error message you get when trying to mount.

---

### Post by nothingspecial on 2008-10-17
Type ```
sudo fdisk -l
``` and post the results here please

---

### Post by khael14 on 2008-10-17
Unable to mount volume
NTFS signature is missing. Failed to mount '/dev/sda1':invalid argument the device '/dev/sda1' doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition ( e.g. /devhda, not /devhda1)? Or the other way around?

---

### Post by khael14 on 2008-10-17
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2373e0c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

---

### Post by nothingspecial on 2008-10-17
What are you trying to mount and how are you trying to mount it?

---

