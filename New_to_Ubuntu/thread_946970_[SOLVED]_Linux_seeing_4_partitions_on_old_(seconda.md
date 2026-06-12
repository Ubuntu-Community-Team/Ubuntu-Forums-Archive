---
title: "[SOLVED] Linux seeing 4 partitions on old (secondary) drive, when only  3 exist"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by akelsall on 2008-10-13
Hello. I'm having an issue mounting one of the partitios off my old Windoze drive. My setup is two SATA drives. The primary is running nothing but Linux (Ubuntu). My secondary drive is my old drive that has Windoze loaded on it. The secondary drive has three partitions (C, D, and E). I wanted to mount these during boot, so I tried adding them to fstab. The device labeled sdb2 is my old "C" drive, sdb5 is my old "D" drive, and sdb6 is my old "E" drive. 

Here's where I'm getting confused. First, my old drive only had three partitions, so why does the output of fdisk -l show 4 (sdb1, sdb2, sdb5, and sdb6)? Secondly I can't seem to find the right syntax to mount /dev/sdb2. I tried autofs and W95 (which is what the output below says it is), but I get error messages telling me "wrong filesystem tpye" (when using autofs), or "unknown filesystem type" (when using W95). Can anyone tell me what the heck sdb2 is??? In reality, it shouldn't even be showing up, since the old drive only had 3 partitions. 

:confused:

Andy

=======================================================================

**Partial output from fdisk -l:**

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27706d20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6486    52098763+   7  HPFS/NTFS
/dev/sdb2            6487       19457   104189557+   f  W95 Ext'd (LBA)
/dev/sdb5            6487       12971    52090731    7  HPFS/NTFS
/dev/sdb6           12972       19457    52098763+   7  HPFS/NTFS


**Partial output from fstab file:**

/dev/sdb1 /media/winroot ntfs-3g rw,nosuid,nodev,noatime,allow_other
/dev/sdb2 /media/winC autofs rw,nosuid,nodev,noatime,allow_other
/dev/sdb5 /media/winD ntfs-3g rw,nosuid,nodev,noatime,allow_other
/dev/sdb6 /media/winE ntfs-3g rw,nosuid,nodev,noatime,allow_other


**Partial output of the mount command:**

/dev/sdb1 on /media/winC type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
/dev/sdb5 on /media/winD type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)
/dev/sdb6 on /media/winE type fuseblk (rw,nosuid,nodev,noatime,allow_other,allow_other,blksize=4096)

---

### Post by drs305 on 2008-10-13
The sdb2 listing in fdisk is an extended partition. Without going into detail, just think of it as a container holding all logical partitions numbered 5 and higher. It doesn't and can't contain data in and of itself, it only holds other partitions. You can't mount it.

If you looked in gparted or another partitioning editor, you would see the extended partition and inside it logical partitions. In the attached screenshot, my extended partition is sda4. Notice the large light blue-bordered box, which is the extended partition. Within it are the individual logical partitions, bordered in dark blue, and a swap partition bordered in red (and also inside the extended partition).


[http://en.wikipedia.org/wiki/Disk_partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning")


Added after akelsall's post below. This is the line he is referencing - note how you can tell it is an extended partition:
```

/dev/sdb2 6487 19457 104189557+ f W95*** Ext'd*** (LBA)

```

---

### Post by akelsall on 2008-10-13
Man, that didn't even cross my mind! ](*,)  Forgot all about the extended partition (guess the "Ext'd" at the end of that line should have been a clue :biggrin:  Thanks for setting me straight!

Andy

---

