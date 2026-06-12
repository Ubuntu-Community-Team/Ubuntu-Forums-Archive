---
title: "Absolute beginner at mounting an external HDD"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Majeh on 2008-10-09
Every time I attempt to mount my external HDD, i get this message:

Cannot Mount the Volume

Mount: wrong fs type, bad option, bad superblock on / dev/sdb1, missing codepage or helper program, or other error  In some cases useful info is found in syslog-try  dmesg | tail or so

As someone's first attempt at Linux after switching from XP, could you help me get acquainted with what this means and what I should try in order to fix this?  Forgive me for being an idiot about this, but I really do want to learn the ins and outs of this OS.

---

### Post by WWSmith36 on 2008-10-09
With the external drive plugged in, please type.

Please open a terminal from the menu Applications-> Accessories-> Terminal and type the following command

sudo fdisk -lu
dmesg | tail

Copy and paste the output here.

---

### Post by Majeh on 2008-10-09
noah@noah-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20f520f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593240   625137344   107772052+   5  Extended
/dev/sda5       409593303   619064774   104735736   83  Linux
/dev/sda6       619064838   625137344     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS
noah@noah-desktop:~$ dmesg|tail
[ 5816.020957] ufs was compiled with read-only support, can't be mounted as read-write
[ 5911.723631] ufs was compiled with read-only support, can't be mounted as read-write
[ 5916.675068] ufs was compiled with read-only support, can't be mounted as read-write
[ 6183.288008] ufs was compiled with read-only support, can't be mounted as read-write
[ 6357.408761] ufs was compiled with read-only support, can't be mounted as read-write
[ 6361.293443] ufs was compiled with read-only support, can't be mounted as read-write
[ 6409.680448] ufs was compiled with read-only support, can't be mounted as read-write
[ 6525.182526] ufs was compiled with read-only support, can't be mounted as read-write
[ 6642.969888] ufs was compiled with read-only support, can't be mounted as read-write
[ 6691.737439] ufs was compiled with read-only support, can't be mounted as read-write
noah@noah-desktop:~$

---

### Post by WWSmith36 on 2008-10-09
It appears that it can only be mounted as read only while the system is trying to automount it as read-write.

You can try to manually mount it as read only.

```
sudo mkdir /media/external
sudo mount -t usf /dev/sda2 /media/external -o ro
```

I don´t have much experience with the usf filesystem.  I am sure that you can force it to mount as read-write but I´m not sure if that could cause any problems.

Whichever OS you last mounted the device might have left the device in a dirty state.  You could try to remount it in that OS and try to disconnect it cleanly.

---

### Post by Majeh on 2008-10-09
Alright, thanks for the help

---

