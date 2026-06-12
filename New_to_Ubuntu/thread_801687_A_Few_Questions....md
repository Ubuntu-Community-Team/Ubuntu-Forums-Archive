---
title: "A Few Questions..."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by mikeMarek on 2008-05-20
1. I have an external hard drive that I backed up all of my files on (I switched from XP to Linux). Whenever I plug it into the USB port, I get an error message saying that it wasn't properly disconnected in Windows, and now won't mount. The error message suggests that I go back into Windows (which isn't an option for me) and properly disconnect the drive, or try to disconnect through the terminal window. I've had no success with that. Any help?

2. I just recently downloaded Beryl (the file name is "aquamarine-0.2.1.tar.bz2"). I am totally new to Linux (just installed Ubuntu yesterday) and am wondering how to install it. Again, any help?

Thanks for much for any help and replies and all is greatly appreciated,
-Mike

---

### Post by tamoneya on 2008-05-20
use the force option:```
sudo mount -t ntfs /dev/sdb1 /windows -o force
```That is assuming that it is device /dev/sdb1 and you want to mount to /windows.  If you dont know what i mean by /dev/sdb1 please post the result of ```
sudo fdisk -l
```and I will help you out.

---

### Post by mikeMarek on 2008-05-20
The forced mount did work, but now I get another error message saying a file is missing.

Also, here's the results for sudo fdisk -l:

```
michael@Michael:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19175   154023156   83  Linux
/dev/sda2           19176       19457     2265165    5  Extended
/dev/sda5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc819c819

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2498    20065153+   7  HPFS/NTFS
michael@Michael:~$ 

```

---

### Post by tamoneya on 2008-05-20
which file does it say is missing specifically.

---

### Post by mikeMarek on 2008-05-20
> **tamoneya said:**
> which file does it say is missing specifically.

Never mind, it started working when I restarted my PC.

Also, would you know how to install Beryl? I've Googled it, but no such luck.

Thanks for all of the help you've been more than extremely helpful! :D <3
-Mike

---

### Post by tamoneya on 2008-05-20
I find that the easiest way to install new themes is with emerald:```
sudo apt-get install emerald
```

---

