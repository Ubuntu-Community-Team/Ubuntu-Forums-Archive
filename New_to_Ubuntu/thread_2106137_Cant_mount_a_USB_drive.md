---
title: "Cant mount a USB drive"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by jonpon on 2013-01-18
Hi 
My laptop sadly died so I've removed the hard drives and connected them to my desktop via USB. The boot drive works fine and I have retrieved all the important stuff, but the other one my 2nd drive (with all my photos on!!!) won't mount I'm getting this message
```
Unable to mount 80 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

When I type "dmesg" I get this which doesn't really help me at all```
[  120.928044] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[  124.453231] VFS: Can't find ext3 filesystem on dev sdb1.
[  226.087701] VFS: Can't find ext3 filesystem on dev sdb1.
[  360.032936] VFS: Can't find ext3 filesystem on dev sdb1.
[ 1478.094749] VFS: Can't find ext3 filesystem on dev sdb1.


```
any suggestions would be much appreciated.

---

### Post by Herman on 2013-01-18
I suggest you try a file system check to begin with, it won't do any harm and if you're lucky it may just fix the problem,  ```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```EDIT: If it doesn't fix the problem it will return an error message. The contents of the error message will probably be helpful to decide which command to try next.

---

### Post by jonpon on 2013-01-18
Hi Herman, Thanks for the reply but
that's not mounting either 
```
getrappel@getrappel-desktop:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
e2fsck: No such file or directory while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by Herman on 2013-01-18
Try this, ```
sudo e2fsck -b 8193 /dev/sdb1
``` If not, this command can be used to tell you where there might be more backup superblocks to replace your corrupted one with, ```
sudo dumpe2fs /dev/sdb1 | grep -i superblock
```

---

### Post by jonpon on 2013-01-18
I unplugged it and plugged back in again, now its called sdg1  !?
This is what I got.

```
getrappel@getrappel-desktop:~$ sudo dumpe2fs /dev/sdg1 | grep -i superblock

[sudo] password for getrappel: 
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdg1
Couldn't find valid filesystem superblock.
getrappel@getrappel-desktop:~$ 

```

---

### Post by Herman on 2013-01-18
Oh, that seems like bad news.  This is an ext series file system of course?   I'm sorry but I think the next step will be to leave the file system as it is and try a file recovery with photorec or some other file recovery software of your choice. I have tried PhotoRec before and it has worked for me. I have not tried every kind of file recovery software, you may have some other one you prefer. To install photorec you need to install TestDisk, and photorec will be installed along with TestDisk as a companion program. ```
sudo apt-get install testdisk
``` I expect Photorec will be able to recover your photos but they will not have the original file names.  There is good instructions at the TestDisk and PhotoRec website for how to use their software.      Here are a few URLs to websites you might find useful, PhotoRec - CG Security, [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)  DataRecovery - Ubuntu Community Docs,  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  How to recover lost files after you accidentally wipe your hard drive by Shawn Hermans, [http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

---

### Post by Herman on 2013-01-18
I imagine you have already done so, but try re- checking your hardware again as USB external hard drives can have all kinds of weird problems. Make sure all connections are clean and tight. They can be fussy about their connection cables or they can have faulty plugs or circuitry.  More than once I have had USB external drives fail to receive sufficient power to spin up properly and on occasions I have found that even by plugging them into a different port on the same computer or using a different USB cable fixed the problem. If you have a sata cable to plug the hard drive in directly to your motherboard and a spare power cable it would eliminate a few potential problems.

---

### Post by jonpon on 2013-01-18
Thanks Herman, 
I already installed testdisk,It was the first thing I got from a google search, Not sure I really understand it though

---

### Post by Herman on 2013-01-18
Okay then, here is one more URL which I think is probably the best of them all for explaining how to use photorec, Recovering Windows files with a Ubuntu CD III: deleted files - Ubuntucat by aysiu, [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by mcduck on 2013-01-18
> **jonpon said:**
> Hi 
My laptop sadly died so I've removed the hard drives and connected them to my desktop via USB. The boot drive works fine and I have retrieved all the important stuff, but the other one my 2nd drive (with all my photos on!!!) won't mount I'm getting this message
```
Unable to mount 80 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

When I type "dmesg" I get this which doesn't really help me at all```
[  120.928044] usb 1-1: reset high speed USB device using ehci_hcd and address 4
[  124.453231] VFS: Can't find ext3 filesystem on dev sdb1.
[  226.087701] VFS: Can't find ext3 filesystem on dev sdb1.
[  360.032936] VFS: Can't find ext3 filesystem on dev sdb1.
[ 1478.094749] VFS: Can't find ext3 filesystem on dev sdb1.


```
any suggestions would be much appreciated.

What filesystem is the drive supposed to be? Based on the output, if you are using the correct device name then it either is something else than Ext2/3/4 or is corrupted.

What does *sudo fdisk -l* say? And also you can run *tail -f /var/log/syslog* and then connect the drive to easily catch information about how the drive is detected...

---

### Post by Noor1101 on 2013-01-18
This sounds a lot like my issue in [my thread]("http://ubuntuforums.org/showthread.php?t=2105904&page=2"). I get almost the same error messages.
Luckily my drive did not have any data on it, but unfortunately I can't format or create a new partition table either. I have come to the conclusion that either the disk is broken, **or its (cheap) external enclosure (casing) is what's causing the problem**.

Have you tried using a different casing? Or connecting it to a different computer? ( I hope I correctly understood that it's an internal drive in a casing)

(I haven't tried using a different casing yet because I lent the only other one I have to someone, and I am waiting to get it back)

Good luck

---

### Post by jonpon on 2013-01-18
sudo fdisk -l says:-

```
getrappel@getrappel-desktop:~$ sudo fdisk -l 
[sudo] password for getrappel: 
Sorry, try again.
[sudo] password for getrappel: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f174f16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS
/dev/sda2            7297       14593    58613122    f  W95 Ext'd (LBA)
/dev/sda5            7297        8321     8233261+   7  HPFS/NTFS
/dev/sda6           13415       14593     9470286    b  W95 FAT32
/dev/sda7            8322       13297    39969688+  83  Linux
/dev/sda8           13298       13414      932864   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026360832 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55f123ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
/dev/sdb2            9730        9730           0    e  W95 FAT16 (LBA)

```
And tail -f /var/log/syslog...
```
getrappel@getrappel-desktop:~$ tail -f /var/log/syslog
Jan 18 18:23:14 getrappel-desktop kernel: [ 1061.651590] sd 4:0:0:0: [sdg] Attached SCSI disk
Jan 18 18:23:22 getrappel-desktop kernel: [ 1069.112032] usb 1-6: reset high speed USB device using ehci_hcd and address 4
Jan 18 18:23:26 getrappel-desktop kernel: [ 1073.371306] VFS: Can't find ext3 filesystem on dev sdg1.
Jan 18 18:31:39 getrappel-desktop kernel: [ 1566.305700] usb 1-6: USB disconnect, address 4
Jan 18 18:31:49 getrappel-desktop kernel: [ 1576.412072] usb 1-6: new high speed USB device using ehci_hcd and address 5
Jan 18 18:31:49 getrappel-desktop kernel: [ 1576.545275] usb 1-6: configuration #1 chosen from 1 choice
Jan 18 18:31:49 getrappel-desktop kernel: [ 1576.553046] scsi5 : SCSI emulation for USB Mass Storage devices
Jan 18 18:31:49 getrappel-desktop kernel: [ 1576.582401] usb-storage: device found at 5
Jan 18 18:31:49 getrappel-desktop kernel: [ 1576.582405] usb-storage: waiting for device to settle before scanning
Jan 18 18:31:53 getrappel-desktop kernel: [ 1580.444303] usb 1-6: USB disconnect, address 5
Jan 18 18:32:17 getrappel-desktop kernel: [ 1603.832069] usb 1-6: new high speed USB device using ehci_hcd and address 6
Jan 18 18:32:17 getrappel-desktop kernel: [ 1603.965259] usb 1-6: configuration #1 chosen from 1 choice
Jan 18 18:32:17 getrappel-desktop kernel: [ 1603.969884] scsi6 : SCSI emulation for USB Mass Storage devices
Jan 18 18:32:17 getrappel-desktop kernel: [ 1603.996150] usb-storage: device found at 6
Jan 18 18:32:17 getrappel-desktop kernel: [ 1603.996154] usb-storage: waiting for device to settle before scanning
Jan 18 18:32:22 getrappel-desktop kernel: [ 1608.998476] usb-storage: device scan complete
Jan 18 18:32:22 getrappel-desktop kernel: [ 1608.999038] scsi 6:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.002873] sd 6:0:0:0: Attached scsi generic sg3 type 0
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.006636] sd 6:0:0:0: [sdg] 156301486 512-byte logical blocks: (80.0 GB/74.5 GiB)
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.007127] sd 6:0:0:0: [sdg] Write Protect is off
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.007132] sd 6:0:0:0: [sdg] Mode Sense: 03 00 00 00
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.007135] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.008488] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.008498]  sdg: sdg1
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.095099] sd 6:0:0:0: [sdg] Assuming drive cache: write through
Jan 18 18:32:22 getrappel-desktop kernel: [ 1609.095110] sd 6:0:0:0: [sdg] Attached SCSI disk
Jan 18 18:32:30 getrappel-desktop kernel: [ 1617.112028] usb 1-6: reset high speed USB device using ehci_hcd and address 6
Jan 18 18:32:33 getrappel-desktop kernel: [ 1620.788020] VFS: Can't find ext3 filesystem on dev sdg1.


```

---

### Post by jonpon on 2013-01-18
> **Noor1101 said:**
> This sounds a lot like my issue in [my thread]("http://ubuntuforums.org/showthread.php?t=2105904&page=2"). I get almost the same error messages.
Luckily my drive did not have any data on it, but unfortunately I can't format or create a new partition table either. I have come to the conclusion that either the disk is broken, **or its (cheap) external enclosure (casing) is what's causing the problem**.

Have you tried using a different casing? Or connecting it to a different computer? ( I hope I correctly understood that it's an internal drive in a casing)

(I haven't tried using a different casing yet because I lent the only other one I have to someone, and I am waiting to get it back)

Good luck
Thanks Noor, I tried a different computer but I only have one enclosure  But it works with my other drive

---

### Post by mcduck on 2013-01-18
That's interesting, was the drive really connected when you ran the fdisk command? It should definitely at least show the drive itself, even if it doesn't manage to find any partitions or filesystems in the drive.

Perhaps there's something wrong with the partition table of the drive (although it should still appear in fdisk!). You could try gpart or some other tool capable of recovering partition tables.

---

