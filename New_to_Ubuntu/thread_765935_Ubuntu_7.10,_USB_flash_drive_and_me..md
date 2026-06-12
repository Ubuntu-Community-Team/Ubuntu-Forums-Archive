---
title: "Ubuntu 7.10, USB flash drive and me."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by marbig on 2008-04-24
The above combination is not working for me at the moment. I have a USB flash drive with an Excel file on it I got from work. Want to access it from my computer at home and use it in OpenOffice. I've been away from Linux for a while so re-classifying myself as a newbie. 
When I plug the drive in nothing comes up on the desktop. If I search for it I'm at a dead end. Still do not fully understand Linux's file system and I don't even know what the flash drive would be called.
Any help really appreciated.
NB. I can do this on my windows XP OS.But would like to learn it on Linux.

---

### Post by jpdamigaman on 2008-04-24
HI I'm quite new to linux.

I got a usb flash drive and pluged it in & it worked out of the box.

What file system is on flash drive?

Is it very big?

My flash drive works in windows xp too.

---

### Post by sam_delta on 2008-04-24
all devices appear under /dev folder inside the filesystem, but they cant be accessed unless you mount them, once mounted, you can actually access the information inside. once mounted, the device should appear under /media folder inside the filesystem.

in my experience, devices such as usb are normally auto-mounted, and you can find them under places>computer, in ubuntu's top pannel.

to manually mount devices :
sudo mount /dev/<device> /media/<any name>

this will mount the device located in /dev into a new folder in /media in order to have acess to your media

remember to unmount the media before removing, you can right click the device and click unmount, to unmount in the terminal type

sudo umount /dev/<device>

sam

---

### Post by ace007 on 2008-04-24
It is possible the drive is not auto-mounting.  Please open a terminal and paste the output of the following

```

sudo fdisk -l

```

Hopefully the drive will appear somewhere in this list.  You can then use the above instructions to manually mount the drive.

---

### Post by marbig on 2008-04-24
> **ace007 said:**
> It is possible the drive is not auto-mounting.  Please open a terminal and paste the output of the following

```

sudo fdisk -l

```Hopefully the drive will appear somewhere in this list.  You can then use the above instructions to manually mount the drive.

```

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04c5439b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       18936   152103388+   7  HPFS/NTFS
/dev/hda2   *       18937       30023    89056327+  83  Linux
/dev/hda3           30024       30401     3036285    5  Extended
/dev/hda5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb486116b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *        4247        4865     4972117+  83  Linux
/dev/hdb2               2        4246    34097962+   f  W95 Ext'd (LBA)
/dev/hdb5               2        4211    33816793+   7  HPFS/NTFS
/dev/hdb6            4212        4246      281106   82  Linux swap / Solaris

Partition table entries are not in disk order 
```I'm not sure what all this means. I have to go on an errand now. But will return to this thread soonests. Thanks.

---

### Post by marbig on 2008-04-25
From running> sudo fdisk -lI cannot see anything for the flash drive [see previous post]. Any other info genuinely appreciated.

---

