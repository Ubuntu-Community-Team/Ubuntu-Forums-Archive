---
title: "[SOLVED] Auto-mounting NTFS partitions"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Pas_sa on 2008-09-17
Hi, I have everything set up rather nicely in Ubuntu to work in tandem with my Windows install (which.. I rarely use now hah..) but there are a few problems.

I keep all my music on my NTFS partitions, and I find these partitions are not automatically mounted after the system is loaded. Normally I forget, and then when I open Rhythmbox, it takes forever to re-add my music to the database.

Sooo yeah, to put it simply, how can I make the partitions automatically mount as the system logs in/boots up?

Thanks!

---

### Post by MegaJim on 2008-09-17
Did you use the ntfs-3g tool to mount them?

I find sometimes it creates fstab entries under /media as opposed to /mnt

The problem with that is that generally, items under /media are not mounted until they are manually triggered to do so/inserted, which is not the right approach in your situation.

So in summary, change your mount points for the drive in question from /media to /mnt and the problem should go away.

---

### Post by halitech on 2008-09-17
can you open a terminal and post back the results of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
```

---

### Post by alienexplorers on 2008-09-17
Please Read This:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by drs305 on 2008-09-17
If you want to try to do it yourself, there is a gui app called pysdm that will let you edit your fstab. The "5 Minute Guide" is here:
[http://ubuntuforums.org/showthread.php?t=872197]("http://ubuntuforums.org/showthread.php?t=872197")

---

### Post by Pas_sa on 2008-09-17
> **MegaJim said:**
> Did you use the ntfs-3g tool to mount them?

I find sometimes it creates fstab entries under /media as opposed to /mnt

The problem with that is that generally, items under /media are not mounted until they are manually triggered to do so/inserted, which is not the right approach in your situation.

So in summary, change your mount points for the drive in question from /media to /mnt and the problem should go away.
It automatically set up my partitions.. I haven't configured anything so wouldn't have the slightest idea of where to start changing things?

> **halitech said:**
> can you open a terminal and post back the results of ```
cat /etc/fstab
``` and ```
sudo fdisk -l
```
cat /etc/fstab gives:
```
andrew@andrewdesktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=950b7866-f6a7-4335-bbfe-08e1a214d379 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=06074c20-25e7-4402-b888-02a83d3ef90f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
andrew@andrewdesktop:~$ 

```

sudo fdisk -l gives:
```
andrew@andrewdesktop:~$ sudo fdisk -l
[sudo] password for andrew: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79578351

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7649    61432560    5  Extended
/dev/sda2   *        7650       35248   221688967+   7  HPFS/NTFS
/dev/sda3           35249       60801   205254472+   7  HPFS/NTFS
/dev/sda5               2        7649    61432528+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49af49ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris
andrew@andrewdesktop:~$ 
```

Thanks for the links to tutorials as well folks, however I want to see if there is a quick fix to my solution first before toying around with something that I've *generally* got working, breaking it in the process :)

---

### Post by drs305 on 2008-09-17
Follow these steps to add the ntfs partitions to fstab. The example is for /dev/sda3. You can repeat the steps for the other ntfs partitons by changing /dev/sda3 to /dev/sdaX with X being a different partition number:

Backup fstab and open for editing:
```
sudo cp /etc/fstab /etc/fstab.old
gksu gedit /etc/fstab 

```		

Add these lines. Change "music" to whatever folder you want your music files mounted in.
```
/dev/sda3 /media/***music*** ntfs-3g uid=1000,umask=022 0 0
```

Make the mountpoints, if they don't exist. Change the name 'music' to whatever you named it above:
```

sudo mkdir /media/***music***

```

Unmount, then remount the partitions (you will get some 'busy' messages, that's ok):
```

sudo umount -a
sudo mount -a

```

Read these links for explantions of fstab and mounting:
[Fstab]("https://help.ubuntu.com/community/Fstab")
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Pas_sa on 2008-09-17
Thanks! Everything is hunky dory now :)

---

