---
title: "how do I automount a particular drive upon bootup?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-28
I want to mount my secondary drive automatically when I log in.....right now I have to click Places > 250.1gB >   (and THEN it mounts it, and away I go...) 

The reason I'm asking, is because the drive is set to be a network share...so it needs to be mounted with administrative priviledges (I would always just leave ```
gksudo nautilus
``` open on the drive, being that the ONLY purpose of this box is to share this drive, nothing more) 


Any help would be GREATLY appreciated! :)

---

### Post by Michael.Godawski on 2008-11-28
First a comprehensive guide on fstab by bodhi.zazen:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

I guess you have to add your drive to the fstab file.
Can you please post the output from:

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by theozzlives on 2008-11-28
yeah it would have to be added to the fstab

---

### Post by B34ST1Y on 2008-11-28
here is the output - ```
serverz0r@serverz0r:~$ sudo fdisk -l

Disk /dev/sda: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4019    32282586   83  Linux
/dev/sda2            4020        4111      738990    5  Extended
/dev/sda5            4020        4111      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
serverz0r@serverz0r:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cafa9502-e66c-4f1e-af74-deaecbcf4fb8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c04c8258-3d76-41ea-bb95-360ac7fed53b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by B34ST1Y on 2008-11-28
so my /etc/fstab looks like this ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cafa9502-e66c-4f1e-af74-deaecbcf4fb8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c04c8258-3d76-41ea-bb95-360ac7fed53b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~                                                                                      
```

so logically then....is this the correct code to add to the bottom of my /etc/fstab ? ```
/dev/sdb         /media/disk
```

? am I missing something?

---

### Post by a0u on 2008-11-28
It seems /dev/sdb1 is the drive you want to mount.

In general, the format for adding new partition info to /etc/fstab is:
```
/dev/sdb1    /media/drive2    ext3    defaults    0    0
```Add the line to the end of /etc/fstab.

The second option  (/media/drive2) is the mount point; you can change this to any directory you wish.  However, you would have to create the directory first before the drive can be mounted.
```
sudo mkdir /media/drive2
```I assume the filesystem is ext3, but change this if I'm wrong.

There are more options you can modify - check the [documentation]("https://help.ubuntu.com/community/Fstab").
> 

[LIST]
[*]sync/async - All I/O to the file system should be done (a)synchronously.
[*]auto - The filesystem can be mounted automatically (at bootup, or when mount is passed the -a option). This is really unnecessary as this is the default action of mount -a anyway.
[*]noauto - The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.
[*]dev/nodev - Interpret/Do not interpret character or block special devices on the file system.
[*]exec / noexec - Permit/Prevent the execution of binaries from the filesystem.
[*]suid/nosuid - Permit/Block the operation of suid, and sgid bits.
[*]ro - Mount read-only.
[*]rw - Mount read-write.
[*]user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden.
[*]nouser - Only permit root to mount the filesystem. This is also a default setting.
[*]_netdev - this is a network device, mount it after bringing up the network. Only valid with fstype nfs.
[/LIST]
I'm assuming defaults should be fine.
> defaults - Use default settings. Equivalent to rw, suid, dev, exec, auto, nouser, async.

The fifth column signifies whether the backup utility dump will backup the filesystem.  Dump is not used often - if in doubt, set to 0 to disable.

The sixth column signifies whether fsck will check the filesystem.  Use 0 to disable, 1 to check first, and 2 to check next (after previous partitions are checked).

---

### Post by a0u on 2008-11-28
> **B34ST1Y said:**
> 
```
/dev/sdb         /media/disk
```? am I missing something?

I believe /dev/sda and /dev/sdb refer to separate *physical* drives, whereas /dev/sda1, /dev/sda5, and /dev/sdb1 refer to individual logical *partitions* within those drives. For technical reasons, you can only mount partitions (i.e., filesystems may differ between partitions).  Hence, if you have a hard drive with three internal partitions, you must mount them separately in /etc/fstab.

---

### Post by B34ST1Y on 2008-11-28
MOST excellent! Thank you so much! [SOLVED]

---

### Post by a0u on 2008-11-28
> **B34ST1Y said:**
> MOST excellent! Thank you so much! [SOLVED]
You're welcome. :)

---

