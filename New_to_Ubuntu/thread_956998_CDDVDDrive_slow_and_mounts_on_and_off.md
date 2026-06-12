---
title: "CD/DVDDrive slow and mounts on and off"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Potts on 2008-10-23
I am having problems with my CD/DVD drive which works fine in Windows but not Ubuntu 8.04.

Sometimes the drive won't mount and when it does mount it is slow.

I'm not sure what info to pass along but I tried to run the drive parimeters and here is what I see.  
 

david@Ubuntu-Linux:~$ sudo hdparm /dev/scd0

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
david@Ubuntu-Linux:~$

---

