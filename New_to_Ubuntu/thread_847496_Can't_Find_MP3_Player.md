---
title: "Can't Find MP3 Player?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-07-02
I have a  Samsung YP-T7J. When I plugged it in, I expected to see something pop up on the desktop; but nothing did. Do I need to install drivers our mount it somehow? Thanks!

I Know it is connected because when I typed lsusb into the terminal this popped up:
> Bus 005 Device 003: ID 04e8:5047 Samsung Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

---

### Post by finer recliner on 2008-07-02
what is the output of ```
sudo fdisk -l 
```?

---

### Post by redfox1160 on 2008-07-02
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9545    76670181   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

```

---

### Post by finer recliner on 2008-07-02
since it is not showing up in your fdisk, the device is not being recognized as a device with a valid filesystem that can be mounted.

try looking at this thread [http://ubuntuforums.org/showthread.php?t=250046&page=3](http://ubuntuforums.org/showthread.php?t=250046&page=3). some of the info may be related to your mp3 player

---

### Post by inagaddadavida on 2008-09-10
I believe I have the same mp3 player as you.  I was able to get mine to work using the MTP connection in a program called Amarok...it is in the repositories.

---

