---
title: "problem when i want copying a file"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by ali10 on 2013-09-24
hi 
i have a problem when i want to copy a file in "sdba3"
i have this problem 

Error while copying to "sda3".
 The destination is read-only.

i use ubuntu 12.4

thanks for everything

---

### Post by whitesmith on 2013-09-24
Please post both your exact copy command (or are you doing it with a GUI?) and the result of ```
sudo fdisk -l
```. Welcome to the forum!

---

### Post by Impavidus on 2013-09-24
You mention sda3. Although it's perfectly legal to call any file sda3, that name usually refers to a partition. Files can be copied to a location in a file system, not directly to a partition. Could you elaborate on that?

---

### Post by Jonathan Precise on 2013-09-24
> **ali10 said:**
> hi 
i have a problem when i want to copy a file in "sdba3"
i have this problem 

Error while copying to "sda3".
 The destination is read-only.

i use ubuntu 12.04

thanks for everything

1) is it /dev/sda3 or /dev/sdb3?

2) Mount the partition:
```
sudo mount -t *filesystem-type* /dev/sd*****3 /_path_/_to_/_mount-point_
```

Find your filesystem in gparted (fat16=fat | fat32=vfat | CD/DVD_(non_UDF)=iso9660). Replace ***** with a or b. Replace /_path_/_to_/_mount-point_ with the path to your mount-point (usually /mnt or a folder in /media, except when using ubuntu 12.10 and above).

Afterwards, copy the file to /_path_/_to_/_mount-point_&#8203;.

---

