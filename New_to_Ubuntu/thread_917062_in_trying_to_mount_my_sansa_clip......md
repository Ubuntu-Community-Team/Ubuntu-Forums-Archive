---
title: "in trying to mount my sansa clip....."
date: 2008-09-11
forum: New to Ubuntu
---

### Post by wayneo on 2008-09-11
In trying to mount my Sansa clip via fourm feedback I seemed to screw something up.
I never did get the clip to work, but now my external hard drive is acting funny.
From a previous session, there is an Icon of my external hd on the desktop even though the hd isnt turned on. I cannot delete it. When trying to delete it I get an error indicating that the volume isnt recognized by HAL.
When I do turn the hd on, it isnt showing me as the owner of it and isnt acting the way it did before I tried in vain to mount the clip.
I used terminal commands to mount the clip, one I remember is lsusb.
Is there any one who can set this right for me? I am sure it is a matter of the proper terminal command.
Thank you for your time and consideration.
All the best,
Wayneo

---

### Post by aysiu on 2008-09-11
Can you plug in the Sansa Clip, paste these commands into the terminal, and then paste the output back here? ```
cat /etc/fstab
sudo fdisk -l
df -h
```

---

### Post by wayneo on 2008-09-11
wayne@wayne-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8dfc7282-6f3e-4b2f-b545-f02b83117e67 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4b4ea8bc-96dc-4ed8-b87a-e6989bec491c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
wayne@wayne-laptop:~$ sudo fdisk -l
[sudo] password for wayne: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4679    37584036   83  Linux
/dev/sda2            4680        4864     1486012+   5  Extended
/dev/sda5            4680        4864     1485981   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ec37bb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdd: 2044 MB, 2044198912 bytes
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?      199216      491461   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?       43188      538843   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      478721      974376   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?           1      931190  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

This is with the Sansa and the external HD plugged in.
Thanks 
Wayneo

---

### Post by aysiu on 2008-09-11
It looks as if something's wrong with the Sansa Clip's partition table: ```
Disk /dev/sdd: 2044 MB, 2044198912 bytes
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.
```

---

### Post by wayneo on 2008-09-11
How about the external HD? How do I go about getting it to see me as the administrator/Owner?
Thanks
Wayneo

---

### Post by aysiu on 2008-09-11
> **wayneo said:**
> How about the external HD? How do I go about getting it to see me as the administrator/Owner?
Thanks
Wayneo
Is that this one? ```
Device Boot Start End Blocks Id System
/dev/sdc1 1 38913 312568641 c W95 FAT32 (LBA)
``` If so, this might help: ```
sudo umount /dev/sdc1
sudo mkdir /media/external
sudo mount -t vfat /dev/sdc1 /media/external -o iocharset=utf8,umask=000
```

---

### Post by wayneo on 2008-09-11
Its this one,

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ec37bb2

---

### Post by aysiu on 2008-09-11
Yeah, try the code I gave you.

---

### Post by wayneo on 2008-09-11
This is what I have..

wayne@wayne-laptop:~$ sudo umount /dev/sdc1
umount: /dev/sdc1: not mounted
wayne@wayne-laptop:~$ sudo mkdir /media/external
mkdir: cannot create directory `/media/external': File exists
wayne@wayne-laptop:~$ sudo mount -t vfat /dev/sdc1 /media/external -o iocharset=utf8,umask=000

---

### Post by wayneo on 2008-09-11
When I go to properties I get "The permissions of the External could not be determined".
Wayneo

---

