---
title: "[SOLVED] installed kde desktop, now need help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-07-01
hi,

i just installed kde for ubuntu so i could switch between that and gnome. however, after the installation, the system can't find/doesn't recognize my external harddrive. suggestions?

---

### Post by ChameleonDave on 2008-07-01
> **jmd9qs said:**
> hi,

i just installed kde for ubuntu so i could switch between that and gnome. however, after the installation, the system can't find/doesn't recognize my external harddrive. suggestions?

Only from KDE or even if you do it from GNOME?

---

### Post by jmd9qs on 2008-07-01
it happens with both. in fact now i cant find it in vista, too. cancel that, drivers just got installed. so it works in vista but not kde or gnome

---

### Post by ChameleonDave on 2008-07-01
> **jmd9qs said:**
> it happens with both. in fact now i cant find it in vista, too. cancel that, drivers just got installed. so it works in vista but not kde or gnome

It's probably nothing to do with installing KDE.  It may be an NTFS issue.  You might want to consider performing a disk check on it in Vista.

In Ubuntu, plug in your drive, and then type these commands in at the command-line terminal.  Paste the output here so that I can get an idea of the situation.

```

sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk*

```

---

### Post by jmd9qs on 2008-07-01
> **ChameleonDave said:**
> It's probably nothing to do with installing KDE.  It may be an NTFS issue.  You might want to consider performing a disk check on it in Vista.

In Ubuntu, plug in your drive, and then type these commands in at the command-line terminal.  Paste the output here so that I can get an idea of the situation.

```

sudo fdisk -l

[PHP]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4191e06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27557   221349368+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           27558       37755    81915435    5  Extended
/dev/sda3           37756       38913     9298800    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5           37270       37755     3903795   82  Linux swap / Solaris
/dev/sda6           27558       37268    78003544+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61670f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001    b  W95 FAT32
[/PHP]
cat /etc/fstab

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5821b866-21a8-4418-b385-bd7cd48dcd1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d0c427b-a14d-40b1-ae73-b79c4daf4246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
[/PHP]
ls -l /dev/disk*

[PHP]total 0
drwxr-xr-x 2 root root 420 2008-07-01 03:07 by-id
drwxr-xr-x 2 root root  80 2008-06-30 20:37 by-label
drwxr-xr-x 2 root root 320 2008-07-01 03:07 by-path
drwxr-xr-x 2 root root 140 2008-07-01 03:07 by-uuid[/PHP]

```

this is the output

---

### Post by jmd9qs on 2008-07-01
wow that looks awful. try this.

jmd9qs@jmd9qs-desktop:~$ sudo fdisk -l
[sudo] password for jmd9qs: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4191e06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27557   221349368+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           27558       37755    81915435    5  Extended
/dev/sda3           37756       38913     9298800    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5           37270       37755     3903795   82  Linux swap / Solaris
/dev/sda6           27558       37268    78003544+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61670f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       60801   488384001    b  W95 FAT32




jmd9qs@jmd9qs-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5821b866-21a8-4418-b385-bd7cd48dcd1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9d0c427b-a14d-40b1-ae73-b79c4daf4246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0


jmd9qs@jmd9qs-desktop:~$ ls -l /dev/disk*
total 0
drwxr-xr-x 2 root root 420 2008-07-01 03:07 by-id
drwxr-xr-x 2 root root  80 2008-06-30 20:37 by-label
drwxr-xr-x 2 root root 320 2008-07-01 03:07 by-path
drwxr-xr-x 2 root root 140 2008-07-01 03:07 by-uuid

---

### Post by ChameleonDave on 2008-07-01
OK, your external drive is sdg1.  However, we can't rely on that to mount it, because drive names change as things are plugged and unplugged.  We need the drive to have a label or UUID.  The "ls -l /dev/disk*" command was supposed to find out label or UUID the drive had.  I am extremely surprised that it returned no information.

To just go ahead and assign a label to your external drive, do the following:

```
sudo apt-get install mtools
```

That installs the program we need.  Then type this:

```
sudo mlabel -i /dev/sdg1 -s ::
```

That should give the current label of the drive, if it has one.

```
sudo mlabel -i /dev/sdg1 ::external
```

That command will set the label to "external".

Now we can tell Ubuntu to recognise this drive.

Type the following:

```
sudo nano /etc/fstab
```

That will open up the fstab file for editing.  You may replace "*nano*" with your favourite text editor (*gedit*, *kate*, *kwrite*, *vim*...).

Add this line to the file:

```
LABEL=external  /media/external  vfat  defaults,rw,exec,user  0 0
```

Replace "external" with whatever the drive label actually is.  Save.

Create the mount point that you declared in the fstab file.  Thus:

```
sudo mkdir /media/external
```

From now on, Ubuntu should recognise that drive.  You can mount it at any time with "sudo mount /media/external" on the command line.  It will probably automount too.

---

