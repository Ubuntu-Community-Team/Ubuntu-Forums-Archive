---
title: "Mountung DVD RAM device"
date: 2008-02-08
forum: Philippine Team
---

### Post by gmarvz on 2008-02-08
greetings, 

   i have a problem, i can't open cd and dvd on my ubuntu gutsy gibbon.. it says "unable to mount device"

here is a copy of my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=91b4d70c-33dc-4f6e-8a9c-a93d186d8a12 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=12DCC76FDCC74BA3 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=5E04368D043667E3 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=f01c9998-44f9-4eb9-b568-7bb3cb5385a8 none            swap    sw              0       0
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

what should i do to fix this? ubuntu detects my dvd drive because i can see it in the lshw list..

---

### Post by vpjr on 2008-02-13
if ubuntu saw the drive itself, then the problem is probably because the dvd or the vcd or the cd itself cannot be mounted by any available application you've installed using the available codecs in your ubuntu pc.

try the following solutions:

1. install VLC
2. get the following packages: libdvdcss2, libdvdnav4, libdvdread3, etc.

---

