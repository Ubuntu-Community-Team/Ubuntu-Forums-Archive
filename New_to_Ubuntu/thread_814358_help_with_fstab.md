---
title: "help with fstab"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-31
sda1, 5, 6, & 7 dont mount.

```
ant2ne@2ne-cygne:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c3855d91-6529-4c9b-96f4-1ee993eb7d25 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d72ace31-5fef-47a9-ac5c-c203c5c29e80 /home           ext3    relatime        0       2
# /dev/sda8
UUID=bedc1740-8f5c-40b9-8bf0-22e9c461a3df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda1	/mnt/sda1	ntfs-3g default 0 0	
/dev/sda5	/mnt/sda5	ext3 	default 0 0
/dev/sda6	/mnt/sda6	exx3	default 0 0
/dev/sda7	/mnt/sda7	ntfs	default 0 0
ant2ne@2ne-cygne:~$ 

```

---

### Post by dracayr on 2008-05-31
I'm not sure, but isn't it supposed to be "defaults" instead of "default"

Edit: just noticed that that's what your /proc sais too

dracayr

---

### Post by chrisccoulson on 2008-05-31
> **dracayr said:**
> I'm not sure, but isn't it supposed to be "defaults" instead of "default"

Edit: just noticed that that's what your /proc sais too

dracayr

You're right - it should be 'defaults'. Also /dev/sda6 has a typo on the filesystem type. It should be 'ext3' instead of 'exx3'

To the OP: Maybe you could post an error message? It might be easier for people to help you then. What is the output of:
```
sudo mount -a
sudo fdisk -l
```

---

### Post by rohitsb on 2008-05-31
Hi,

If I remember right, the defaults in fstab corresponds to nouser. Also, I see that the auto option is missing (is this part of defaults) ?. Perhaps that is the reason the partitions are not mounting ?
try something like:

/dev/sda7	/mnt/sda7	ntfs	rw,auto,user 0 0

---

### Post by The Cog on 2008-05-31
> **rohitsb said:**
> Hi,

If I remember right, the defaults in fstab corresponds to nouser. Also, I see that the auto option is missing (is this part of defaults) ?. Perhaps that is the reason the partitions are not mounting ?
try something like:

/dev/sda7	/mnt/sda7	ntfs	rw,auto,user 0 0

I think auto is the default - use noauto if you don't want it to mount at boot.

---

### Post by ant2ne on 2008-06-01
I made the suggested changes. Everything now mounts except /mnt/sda6


```
ant2ne@2ne-cygne:~$ sudo mount -a
[sudo] password for ant2ne: 
ant2ne@2ne-cygne:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57515751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1920    15422368+   7  HPFS/NTFS
/dev/sda3            1921        5099    25535317+  83  Linux
/dev/sda4            5100       24321   154400715    5  Extended
/dev/sda5            5100        8286    25599546   83  Linux
/dev/sda6            8287       17673    75401046   83  Linux
/dev/sda7           17674       23776    49022316    7  HPFS/NTFS
/dev/sda8           23777       24321     4377681   82  Linux swap / Solaris
ant2ne@2ne-cygne:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c3855d91-6529-4c9b-96f4-1ee993eb7d25 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d72ace31-5fef-47a9-ac5c-c203c5c29e80 /home           ext3    relatime        0       2
# /dev/sda8
UUID=bedc1740-8f5c-40b9-8bf0-22e9c461a3df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda1	/mnt/sda1	ntfs-3g defaults 0 0	
/dev/sda5	/mnt/sda5	ext3 	defaults 0 0
/dev/sda6	/mnt/sda6	ext3	defaults 0 0
/dev/sda7	/mnt/sda7	ntfs	defaults 0 0
ant2ne@2ne-cygne:~$ 

```

---

