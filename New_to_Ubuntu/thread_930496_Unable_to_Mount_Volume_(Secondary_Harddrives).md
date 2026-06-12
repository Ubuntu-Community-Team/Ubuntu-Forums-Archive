---
title: "Unable to Mount Volume (Secondary Harddrives)"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Iwneferi on 2008-09-26
I recently switched to Ubuntu from XP Lite. I have three harddrives. The only one that is being properly read by Hardy Heron is the one on which it is installed. The other two harddrives show up in my "Places" drop-down menu, but do not appear to be properly mounted. When I attempt to open them, I get an error message "Unable to mount the volume 'The Library'. Details> Failed to read last sector (321653366): Invalid argument...' and many other words. But you get the picture.

I tried to get help in the hardware section of the forums, but it doesn't seem to be active enough to generate help with complicated issues.

Can anyone here help me get my harddrives working properly?

Thanks in Advance!

~Missy~

---

### Post by Peter09 on 2008-09-26
type ```
df
``` in a terminal and post the output here

---

### Post by kpkeerthi on 2008-09-26
> **Iwneferi said:**
> I recently switched to Ubuntu from XP Lite. I have three harddrives. The only one that is being properly read by Hardy Heron is the one on which it is installed. The other two harddrives show up in my "Places" drop-down menu, but do not appear to be properly mounted. When I attempt to open them, I get an error message "Unable to mount the volume 'The Library'. Details> Failed to read last sector (321653366): Invalid argument...' and many other words. But you get the picture.

I tried to get help in the hardware section of the forums, but it doesn't seem to be active enough to generate help with complicated issues.

Can anyone here help me get my harddrives working properly?

Thanks in Advance!

~Missy~

Post the output of below commands:
```
sudo fdisk -l
```
```
mount
```
Let us know which partition(s) you are trying to mount.

---

### Post by Iwneferi on 2008-09-26
df:

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76400416   6299444  66250596   9% /
varrun                  517688       104    517584   1% /var/run
varlock                 517688         0    517688   0% /var/lock
udev                    517688        76    517612   1% /dev
devshm                  517688        48    517640   1% /dev/shm
lrm                     517688     39760    477928   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      76400416   6299444  66250596   9% /home/iwneferi/.gvfs
/dev/sdd1               982016    815120    166896  84% /media/Sansa c240

sudo fdisk -l:

> Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f4f6f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e827e82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2089    16778241    7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e827e82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2089    16778241    7  HPFS/NTFS

Disk /dev/sdd: 1027 MB, 1027342336 bytes
32 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         991      982272+   6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 16, 16) logical=(0, 16, 32)
Partition 1 has different physical/logical endings:
     phys=(122, 89, 31) logical=(990, 22, 44)
Partition 1 does not end on cylinder boundary.
/dev/sdd2             991        1012       20480   84  OS/2 hidden C: drive
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(122, 89, 32) logical=(990, 22, 45)
Partition 2 has different physical/logical endings:
     phys=(124, 229, 41) logical=(1011, 11, 22)
Partition 2 does not end on cylinder boundary.

mount:

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/iwneferi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=iwneferi)
/dev/sdd1 on /media/Sansa c240 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

I am trying to mount drives sdb and sdc. I do have problems reading my sansa as well (not the same problems), but I will work on that one after I fix the more important issue of my storage drives. FYI: I'd prefer to keep the data on them if at all possible.

---

### Post by kpkeerthi on 2008-09-26
To mount NTFS volumes, see [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Iwneferi on 2008-09-26
I followed the directions on your link, and now my error message reads:

> You are not priveledged to mount the volume 'The Library'.

---

### Post by Frak on 2008-09-26
Precede all of your commands with sudo, such as

sudo mount X

---

### Post by Iwneferi on 2008-09-26
Ok, then could you tell me what command would I use in the terminal? Currently, I have just tried to access my drives via the "places" menu.

---

### Post by Iwneferi on 2008-09-26
Bump

---

### Post by Frak on 2008-09-26
```
sudo mount -t ntfs-3g /dev/<drive> /media/Windows<?> -o umask=0,nls=utf8
```

<drive> is your drive, such as mine is sda1 (1st partition (1) on first hard disk (a)

<?> is your mount location. Yours could possibly even /mnt/ihatewindowsbutimountitanyway. I don't know, just be sure to "sudo mkdir <mount directory used here> first.

---

### Post by Iwneferi on 2008-09-27
I tired, and the response was:

> NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

So... I don't have a valid NTFS? How do I fix that?

---

### Post by Frak on 2008-09-27
Again, while sdb refers to the drive remember to append the partition number. (sd - sata drive, unless using libata, which labels all drives sd, b, being 2nd HD, so sdb, second hard drive, then 1, which is 2nd hard drive, 1st partition.)

You would use sdb1, not sdb.

---

### Post by Iwneferi on 2008-09-27
In that case, we are back to square one:

> Failed to read last sector (781417601): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


---

### Post by Frak on 2008-09-27
Try /dev/hdb1, and see what happens. I'll help you to the fullest of my functioning brain. :)

---

### Post by Iwneferi on 2008-09-28
> ntfs-3g: Failed to access volume '/dev/hdb2': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.


:~$ /sbin/mount.ntfs-3g --help

ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

When I type in "sudo fdisk -l" it tells me that my drives are sda sdb and sdc. I am trying to mount the second two. 

I realize that my computer seems to be doing something crazy and unusual. I appreciate any help you can offer.

Thanks again.

---

### Post by Iwneferi on 2008-09-28
It just occured to me that it is probably important to tell you that all of my harddrives are IDE.

Might that be where the problem lay?

---

### Post by Iwneferi on 2008-10-01
bump

---

### Post by kpkeerthi on 2008-10-01
Post the command (and NOT just the output you are getting) you are using to mount the NTFS partitions.

---

### Post by kpkeerthi on 2008-10-01
1. Create a folder where you want the partition mounted
```
sudo mkdir /media/WindowsSDB
```

2. Mount the partition:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/WindowsSDB
```

You should see a shortcut on your desktop. Post back errors if any.
* /media/WindowsSDB is your mountpoint. You can change it whatever you want. Eg: /media/Windows. Just make sure you use the same mount point in both the commands above

---

### Post by vanadium on 2008-10-01
To avoid the thread becoming difficult to follow, always post back the commands and their output. Also, let us continue to handle one problem at a time, which currently is getting your drive /dev/sdb1 to mount.

The output of your mount command to me suggests that the partition is not at all recognized as ntfs, although the output of fdisk show that it is labeled as such. To make sure that the format is not another one, try the mount command without the file system option (i.e. let Linux auto-determine the file system):

```

sudo mount /dev/sdb1 /media/WindowsSDB

```

Post the output here. I doubt that will work though. To me, it looks like your volume is badly corrupted and probably will need to be reformatted.

---

### Post by Iwneferi on 2008-10-03
```
sudo mount /dev/sdb1 /media/WindowsSDB
```

> Failed to read last sector (781417601): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

My drives did not seem to have any problems before I installed linux. I'm really hoping I wont have to reformat them. Mostly because it's just such a pain to do so.

But thanx, regardless.

~Missy~

---

### Post by Iwneferi on 2008-10-05
bump

---

### Post by Frak on 2008-10-05
Try going into the recovery console (pop in your Windows CD and rebooting). When the CD boots, wait until it prompts you to press r for the recovery console, press r of course. When it gets to the console, log in (yes, Windows makes you log in to use recovery system) and run:

```
chkdsk /R
```

This will:
1. Check the files for damage (first run)
2. Scan the file system for errors (second run)
3. Fix the errors (third run)
4. Scan each sector for errors and repair them (fourth and last run)

It will take a LONG time depending on your drive, but it should fix the not being able to mount volume issue.

See you on the other side :)

---

### Post by Iwneferi on 2008-10-06
Thanks. I will start the process, and let you know how it goes.

---

