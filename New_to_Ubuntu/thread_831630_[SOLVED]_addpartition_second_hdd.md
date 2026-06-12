---
title: "[SOLVED] add/partition second hdd"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by hive225 on 2008-06-17
Hello. I am brand new to ubuntu, and I am trying to add a second hardrive.

I have been searching around and doing LOTS of reading but I can't seem to find what I need. I briefly read [adding second HDD to filesystem]("http://ubuntuforums.org/showthread.php?t=831105") but the information that was posted seems to be for someone using a GUI.

Can anyone offer any help or maybe a link?

---

### Post by cdtech on 2008-06-17
Is it an external or an internal drive?

You can just type on a command line:
sudo fdisk -l
To view the drives and to see which one you need to add to your /etc/fstab file.

You'll need to add it to your fstab file for it to auto mount during boot.

---

### Post by hive225 on 2008-06-17
It's internal.

```
hive225@deloris:~$ sudo fdisk -l
[sudo] password for hive225: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xa23fa23f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         610     4611568+   7  HPFS/NTFS
/dev/sda2             611        5165    34435800    f  W95 Ext'd (LBA)
/dev/sda5             611         746     1028128+   7  HPFS/NTFS
/dev/sda6             747        5165    33407608+   7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x254b254a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3562    28611733+  83  Linux
/dev/sdb2            3563        3654      738990    5  Extended
/dev/sdb5            3563        3654      738958+  82  Linux swap / Solaris
hive225@deloris:~$ 

```

Disk /dev/sda: 40.0 GB is the hardrive I wish to add. (old windows)

---

### Post by logos34 on 2008-06-17
If it's an internal drive, then add it to fstab like cdtech just said.  Don't forget to make the mountpoint.  And if you want to use 'UUID=', get the latter with any of the following:

sudo blkid

sudo vol_id /dev/sda?

ls -l /dev/disk/by-uuid

EDIT:

just saw your last post.

if ntfs use ntfs-config.
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by hive225 on 2008-06-17
okay I think I can manage to mount the drive once I get it formatted, but how do I do that? 

fdisk? I keep reading guides and everything I seem to be reading is for systems using GUI's. I finally ended up reading [Move /home to it's own partition <<Ubuntu Blog]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") (which I guess I need to do) but it skips the part I need!

---

### Post by cdtech on 2008-06-17
If you want to format it for Linux then:

$ sudo mkfs.ext3 /dev/yourdevice

[B]P.S.
You can also create an MS-DOS/Windows XP file system under Linux, enter:
$ sudo mkfs.vfat /dev/yourdevice[/B]

---

### Post by hive225 on 2008-06-17
so to format my HDD for use with ubutu use ```
$ sudo mkfs.ext3 /dev/sda
```

then read the guides on how to mount it?

edit: The pyschochats.net page on partition planning doesn't work. Is there a similar guide somewhere else that someone could point me to?

---

### Post by cdtech on 2008-06-17
Yes that's correct. Be absolutely sure that the dev sda is the correct one.

Be sure to create a mount point such as /mnt/storage (or whatever).

########## your newly formatted drive sda1 - 40G
/dev/sda1   /mnt/storage    ext3     defaults        0       1

Good luck....

---

### Post by hive225 on 2008-06-17
Much thanks to all!

Edit: I found the official ubuntu doc. (oops) to be the most helpful.[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

---

