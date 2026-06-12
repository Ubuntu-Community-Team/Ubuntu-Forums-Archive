---
title: "can't find external to mount it"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by spotsworth on 2008-11-18
hi,

my external is not mounting, and i know i could figure this out on my own if i didn't have a serious headache, but i do, and i need to back-up stuff, so help would be greatly appreciated..

fdisk -l:
```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2938    23559322+  83  Linux
/dev/sda3            2939        6935    32105902+  83  Linux
/dev/sda4            6936        7113     1429785    5  Extended
/dev/sda5            6936        7113     1429753+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6371ce4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7296    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5               2        7296    58597056    b  W95 FAT32
```


cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e5a3e7a3-aefe-4aa4-b7a3-610699c4e3e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-0310  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=d1375ee7-9ef9-46da-8dd2-8f1c3bc6e6f8 /media/sda2     ext3    defaults  0       2
# /dev/sda5
UUID=3041a4ed-bf51-4f1d-a53b-806a9c7a4306 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

i don't see the external in here...but my brain isn't working at this moment...

-spots

---

### Post by spotsworth on 2008-11-18
i figured out 1 thing, it's a I/O issue, but that's definately something i''m lost on anyway...

---

