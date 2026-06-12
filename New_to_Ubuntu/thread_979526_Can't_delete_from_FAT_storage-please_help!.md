---
title: "Can't delete from FAT storage-please help!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2008-11-12
So, I've got some external storage devices (SD cards, memory sticks) that are formatted in FAT so that they'll work with other devices.  Whenever I try to delete files from them in Ubuntu, it removes that much space from the total capacity is well.  So, if I delete a 2GB file from a 4GB card, for example, it will say I have 0 of 2GB free.  Any thoughts?

---

### Post by Crafty Kisses on 2008-11-12
Paste this command in the terminal:
```
dmesg | tail
```
Then post the results back here at the forums.

---

### Post by unknownwarrior33 on 2008-11-12
Here it is:

> [  148.624694] type=1503 audit(1226544266.428:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6190 profile="/usr/sbin/cupsd"
[  148.624706] type=1503 audit(1226544266.428:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6190 profile="/usr/sbin/cupsd"
[  148.624851] type=1503 audit(1226544266.428:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6190 profile="/usr/sbin/cupsd"
[  148.624865] type=1503 audit(1226544266.428:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6190 profile="/usr/sbin/cupsd"
[  148.624883] type=1503 audit(1226544266.428:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6190 profile="/usr/sbin/cupsd"
[  300.987927] CE: hpet increasing min_delta_ns to 22500 nsec
[  301.053351] CE: hpet increasing min_delta_ns to 33750 nsec
[  308.139969] CE: hpet increasing min_delta_ns to 50624 nsec
[  403.153275] CE: hpet increasing min_delta_ns to 75936 nsec
[  408.997396] CE: hpet increasing min_delta_ns to 113904 nsec


---

### Post by unknownwarrior33 on 2008-11-12
So, my friend things that the problem is that I haven't been emptying the trash before removing the drive.  That might be it; I'll try it and let you know.

---

### Post by unknownwarrior33 on 2008-11-13
Yup, that was it.  But thanks!

---

