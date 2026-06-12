---
title: "Mount existing ext3 volume to new linux install"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by BigNotch44 on 2008-09-11
Hey all.  I've been banging my head on this for a few hours...:confused: so why not ask the community.  I moved a hard drive from an old ubuntu system into a new system.  The hd already has data on it and all I want to do is mount it to a new folder in my new Ubuntu 8.04 system.  I've tried mount, but for some reason when I run:
```
sudo /sbin/fdisk -l
```
The hard drive of interest doesn't show up.  Can someone kindly assist me?

Thanks!

---

### Post by skippuff54 on 2008-09-11
maybe it's a hardware issue. do u know that ur IDE cables are ok? are the jumpers on the drive in the correct place? i'm guessin u want this to be a slave drive

---

### Post by ukripper on 2008-09-11
As suggested in earlier post check your cables and jumper settings may be try finding in BIOS if BIOS detects your drive first. If it does then follow the follwoing-


can you post output of the followign commands only if your BIOS detects your drive:
```
dmesg | less

```
```
sudo fdisk -l
```

```
sudo blkid
```

```
gedit /etc/fstab
```

---

### Post by dentharg on 2008-09-11
If the new system is all SATA but you have a PATA slot emulated (like JMicron os my Asus p5b) see whether it is in correct mode in BIOS. Also a driver for such must be loaded.

---

### Post by MsTBWLZQ on 2008-09-11
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by BigNotch44 on 2008-09-12
I checked for hardware issues, and none was found.  The drive was found in my bios and AHCI init.  I was just using this drive and its contents a few days ago in another ubuntu system so I'm sure that all is working.  Ok, here's the output I got from Ukripper's post (not including dmesg | less b/c output was too big):

```
sudo fdisk -l
```
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45843fd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       24792   198892732+   5  Extended
/dev/sda5              32       24792   198892701   8e  Linux LVM

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0deb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

```
```
sudo blkid
```
```
/dev/mapper/ServerNotch-swap_1: TYPE="swap" UUID="7eeb2692-a511-4bcd-b904-c72094d561d5" 
/dev/mapper/ServerNotch-root: UUID="b0dc9429-9e4d-4b10-876f-077bced94665" TYPE="ext3" 
/dev/sda1: UUID="5d29b15e-41c6-4723-bb3f-5036d1911be8" TYPE="ext3" 
/dev/sda5: UUID="C0kOEj-OOKZ-hnZy-aW0c-RUlr-Fvzs-uYfTy1" TYPE="lvm2pv" 
/dev/sdb1: UUID="67227e09-1886-4f3a-9a86-4ac11e643ab6" SEC_TYPE="ext2" TYPE="ext3" 

```
```
/etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/ServerNotch-root
UUID=b0dc9429-9e4d-4b10-876f-077bced94665 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=5d29b15e-41c6-4723-bb3f-5036d1911be8 /boot           ext3    relatime        0       2
# /dev/mapper/ServerNotch-swap_1
UUID=7eeb2692-a511-4bcd-b904-c72094d561d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

The drive that I want to mount is /dev/sdb.  Now that it's showing up in 'fdisk', I'm sure its something pretty easy.  I just want to mount it to a folder without harming its contents.  Thanks all for the help.:cool:

---

### Post by dentharg on 2008-09-12
Errm..

sudo mkdir /mnt/old_drive
sudo mount -t auto /dev/sdb1 /mnt/old_drive

that's what you need?

---

### Post by ukripper on 2008-09-12
Create new directory :
```
sudo mkdir /media/old_drive
```

then open fstab:
```
sudo gedit /etc/fstab
```

now add the below line to the fstab at the bottom:

```
UUID=67227e09-1886-4f3a-9a86-4ac11e643ab6	/media/old_drive	             ext3    relatime,errors=remount-ro 0
```

Now when you reboot your new drive will be mounted by itself.

---

### Post by BigNotch44 on 2008-09-13
=D> Thanks guys!  I got it mounted and none of the data was lost.  I even got samba running with it perfectly fine.

---

