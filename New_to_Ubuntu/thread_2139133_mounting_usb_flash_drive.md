---
title: "mounting usb flash drive"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Shane Lovett on 2013-04-26
**I cannot mount my usb flash drive although I can see it in lsusb.**

---

### Post by slickymaster on 2013-04-26
Hi, Shane Lovett, be welcome to the forums.

Try to mount it through command line. First see in what filesystem is your USB formatted with:
```
sudo fdisk -l
```After that you need to create the mount point:```
sudo mkdir /media/my_usb
```Finally you just have to mount it. Assuming it's a FAT32 USB:
```
sudo mount -t vfat /dev/sdb1 /media/my_usb -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```
If your drive is NTFS formatted then you'll mount it with:```
sudo mount -t ntfs-3g /dev/sdb1 /media/my_usb
```

Another option would be to use **pmount**, a program available in the repositories.

---

