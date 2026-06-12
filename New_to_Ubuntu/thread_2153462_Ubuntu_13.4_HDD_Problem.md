---
title: "Ubuntu 13.4 HDD Problem"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by Esperos on 2013-06-11
So I use ubuntu for over a month(due to a college project) and Im totaly satisfied. I had the version 12.04 and now Im on 13.04. My pc is dual boot(windows 8 and ubuntu) and the problem is that i cant access my win8 partition through ubuntu, and when I try to i get an error message: 

```
Error mounting /dev/sda3 at /media/nikos/ACER: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/nikos/ACER"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

Its quite annoying because sometimes I want to use files that are in my other partiotion and its no possiblea and the thing is I shut down my pc properly everytime. What should I do? 

ps: I searched the forum but i didnt manage to find anything about that! :)

Acer Asprire 5740G
Intel® Core™ i3 CPU M 330 @ 2.13GHz × 4 
Gallium 0.4 on AMD CEDAR
Ubuntu 13.04 64-bit
HDD: 30GB RAM:4GB

---

### Post by steeldriver on 2013-06-11
Hello and welcome to the forum

That's likely a result of Windows 8's 'fast startup' feature - you will need to boot back into Windows and turn that feature off

[http://askubuntu.com/questions/291864/cannot-mount-ntfs-partition-in-ubuntu-13-04](http://askubuntu.com/questions/291864/cannot-mount-ntfs-partition-in-ubuntu-13-04)

---

### Post by Esperos on 2013-06-11
Thanks a lot, after i disabled it, it works!!!

---

### Post by gigenieks on 2013-06-11
Worked for me too.

---

