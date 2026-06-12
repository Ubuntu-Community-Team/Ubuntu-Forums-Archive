---
title: "How do I auto-mount an NTFS partition"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Toribor on 2008-07-05
I am running a dell laptop with a 160gb internal hard drive with oodles of partitions. For the most part I have 20gb of EXT3 for Ubuntu, and the rest (minus small dell partitions and Ubuntu swap file) an NTFS partition with Windows Vista. I've looked up other guides on auto-mounting drives and kind of have a general idea but thought it would be safer to ask. Is it possible to set up the command to force mount the drive in case Windows is shut down improperly?

This is the result I get from "Sudo fdisk -l"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485756    7  HPFS/NTFS
/dev/sda3   *        1313       16445   121549805    7  HPFS/NTFS
/dev/sda4           16446       19458    24194531    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           19197       19458     2096128   dd  Unknown
/dev/sda6           16446       19076    21133476   83  Linux
/dev/sda7           19077       19196      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6b42d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2433       60802   468850312    b  W95 FAT32

```

I believe the drive I want to auto mount is the larger NTFS partition, "/dev/sda3". What (and where exactly) do I put the command in /ect/fstab? Also, if I wanted to auto-force-mount /dev/sdb1, my Maxtor external will that cause any problems when the drive is missing and is that possible? (I know the USB drive mounts automatically but if it isn't removed properly which it often isn't it wont mount and typing in the force mount commands is a pain)

Thank you in advance for helping!

---

### Post by sharks on 2008-07-05
[www.tweako.com/automount_ntfs_drive_in_ubuntu](www.tweako.com/automount_ntfs_drive_in_ubuntu)
[www.wiki.sabayonlinux.org/index.php?title=HOWTO:_Automount_ntfs_paritions_as_read/write](www.wiki.sabayonlinux.org/index.php?title=HOWTO:_Automount_ntfs_paritions_as_read/write)
[www.ubuntuforums.org/showthread.php?t=555479](www.ubuntuforums.org/showthread.php?t=555479)

---

### Post by crjackson on 2008-07-05
> **Toribor said:**
> I am running a dell laptop with a 160gb internal hard drive with oodles of partitions. For the most part I have 20gb of EXT3 for Ubuntu, and the rest (minus small dell partitions and Ubuntu swap file) an NTFS partition with Windows Vista. I've looked up other guides on auto-mounting drives and kind of have a general idea but thought it would be safer to ask. Is it possible to set up the command to force mount the drive in case Windows is shut down improperly?

This is the result I get from "Sudo fdisk -l"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485756    7  HPFS/NTFS
/dev/sda3   *        1313       16445   121549805    7  HPFS/NTFS
/dev/sda4           16446       19458    24194531    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           19197       19458     2096128   dd  Unknown
/dev/sda6           16446       19076    21133476   83  Linux
/dev/sda7           19077       19196      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6b42d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2433       60802   468850312    b  W95 FAT32

```

I believe the drive I want to auto mount is the larger NTFS partition, "/dev/sda3". What (and where exactly) do I put the command in /ect/fstab? Also, if I wanted to auto-force-mount /dev/sdb1, my Maxtor external will that cause any problems when the drive is missing and is that possible? (I know the USB drive mounts automatically but if it isn't removed properly which it often isn't it wont mount and typing in the force mount commands is a pain)

Thank you in advance for helping!

```
sudo aptitude install ntfs-config
```

---

### Post by ChameleonDave on 2008-07-05
> **Toribor said:**
> I am running a dell laptop with a 160gb internal hard drive with oodles of partitions. For the most part I have 20gb of EXT3 for Ubuntu, and the rest (minus small dell partitions and Ubuntu swap file) an NTFS partition with Windows Vista. I've looked up other guides on auto-mounting drives and kind of have a general idea but thought it would be safer to ask. Is it possible to set up the command to force mount the drive in case Windows is shut down improperly?

This is the result I get from "Sudo fdisk -l"
I believe the drive I want to auto mount is the larger NTFS partition, "/dev/sda3". What (and where exactly) do I put the command in /ect/fstab? Also, if I wanted to auto-force-mount /dev/sdb1, my Maxtor external will that cause any problems when the drive is missing and is that possible? (I know the USB drive mounts automatically but if it isn't removed properly which it often isn't it wont mount and typing in the force mount commands is a pain)

Thank you in advance for helping!

There are threads on this forum with almost exactly the same issue.  Just search for them.

---

### Post by Toribor on 2008-07-05
I tried that already. I mentioned that I did find people with similar issues but no one seemed to have quite the same situation as me so I was worried I'd mess something up.

---

### Post by Troll_the_Great on 2008-07-05
Install ntfs-config and you won't have any problems.Have a look here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Cheers!

---

### Post by ChameleonDave on 2008-07-06
What about this thread?

[http://ubuntuforums.org/showthread.php?t=843994](http://ubuntuforums.org/showthread.php?t=843994)

---

### Post by aktiwers on 2008-07-06
Start by installing ntfs support:
```
sudo apt-get install ntfs-3g
```Then create 2 folders to mount them on in /media/
```
sudo mkdir /media/Disk1
```and
```
sudo mkdir /media/Disk2
```Then open your fstab.
```
gksudo  gedit /etc/fstab
```[FONT=monospace]And add these lines:
[/FONT]> [FONT=monospace]
#/dev/sda2
[/FONT]/dev/sda2  /media/Disk1  ntfs  defaults  0 0[FONT=monospace] 
[/FONT]
#/dev/sda3
/dev/sda3  /media/Disk2  ntfs  defaults  0 0 to the end of the file and Save the document. Then type in Terminal:
```
sudo mount -a
```and you should be good to go :)

You can offcause change the "Disk1" and "Disk2" names in both those commands, to a more suitable name. That is the name your partition will be called on the system(mounted on).

---

### Post by ChameleonDave on 2008-07-06
> **Toribor said:**
> What (and where exactly) do I put the command in /ect/fstab? Also, if I wanted to auto-force-mount /dev/sdb1, my Maxtor external will that cause any problems when the drive is missing and is that possible? ... typing in the force mount commands is a pain)

The order of lines in fstab is not significant.  Anything can go anywhere.  It's good to keep the file logical and easy to read, though.  The lines beginning with the hash sign are comments, and can be used to remind yourself of what refers to what.

Whenever possible, make fstab identify partitions with "**LABEL=***XXXX*"; it is the best and clearest way of doing so.  If the drive in question has no label, then use "**UUID=***XXXX*" instead; it is less legible, but still good.  The least desirable option is to refer to them with "**/dev/***XXXX*"; the problem with it is that the identifier may change if you add drives, remove partitions, etc.

To get info on the labels and UUIDs of your drives, enter either of the following commands.  One of them requires root access.

```

ls -l /dev/disk/*

sudo blkid

```

The other thing about fstab is that you cannot make anything force-mount.  By definition, forcing is not done automatically.  It's something you do by typing a command in, and requires root access.  Each time, a human being must and should enter a password for it to happen.

NTFS is a tricky thing, and regularly force-mounting it after it is improperly shut down by Windows is inadvisable.

---

