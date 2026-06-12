---
title: "Cannot see other HDD"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by ButchMel on 2012-03-17
Hi,
First I must say I'm *totally* new to Linux and Ubuntu. 

I installed Ubuntu Server 10.04.4 (only: no other OS) on a Pentium 4 machine.  I intend to use it as file server, but occasionnally as a PC - so I also installed the graphical interface (Gnome). 

I can see the 2 small HDD which were present at installation.

However, being an old machine, I added a PCI card (PATA) so to be able to add 2 large HDD eventually. (Card is: Sabrent, 4-port SATA PCI Host Controller with RAID function, but I do not intend to use RAID function for now). Oh and I also replaced the Power supply so I could have power through SATA cables. 

While I see the card appearing in the disk utility, I do not see any HDD that I attach to it. I tried both the external connectors and the internal connectors. Don't see it in the Mount Manager either. And... must now add I do not see it in BIOS either....

EDIT: One more factor, if this can rings a bell: prior to install Ubuntu, I physically removed the HDD that contained Windows XP. It was (also) an IDE drive as the two being seen.  Was probably 'master' ??... Could this explain something here (why I can't see new drives in BIOS) ?

Both drives I tried are NTFS. I installed NTFS Configuration Tool also.  One of the drives I tried is 1 TB, the other was only 160 GB. The disks are 'physically' working (I can sense it). 

What am I missing? 

Thanks,


System:
Motherboard: Asus P4B533
Pentium 4, 1.6 Ghz, 2GB memory
Graphic card: Matrox Millenium G450 AGP
OS: Ubuntu Server 10.04.4 with Gnome interface

UPDATE:
MORE after hours of struggling with it.

I have tried the following:

- disconnected HDD that contains OS. Of course hanged at boot-up but here's the info:

Detecting Primary Master : none
Detecting Primary Slave: DVD-RW...
Detecting Secondary Master: none
Detecting Secondary slave: WDC ....
Secondary Slave drive fails

So no sign here yet from my newly connected drive on the SATA PCI card.

Then I tried to simply remove jumpers from both IDE drives... And nothing boot.
Tried to put the one on the drive containing OS only, not the other IDE drive - still impossible to boot.

So I put both back in place as they were initially. Have no additional idea what to do with it really...

In BIOS all drives are set to 'Auto'

---

### Post by 2F4U on 2012-03-17
Did you check the log files if any error messages occurred?

---

### Post by ajgreeny on 2012-03-17
What does ```
sudo fdisk -l
```run in a terminal tell you; it should list all the disks with their partitions and sizes, though you may find the partition sizes difficult to understand, eg
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306       19668   147500797+  83  Linux
/dev/sda4           19669       19929     2096452    5  Extended
/dev/sda5           19669       19929     2096451   82  Linux swap / Solaris
```
In fact, in the Blocks column, it is approximately 1,000,000 per GB, so my sda1 which is 9.9GB shows 10,482,381 blocks.

---

### Post by ButchMel on 2012-03-17
> **ajgreeny said:**
> What does ```
sudo fdisk -l
```run in a terminal tell you; it should list all the disks with their partitions and sizes, though you may find the partition sizes difficult to understand, eg
```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd44cd44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306       19668   147500797+  83  Linux
/dev/sda4           19669       19929     2096452    5  Extended
/dev/sda5           19669       19929     2096451   82  Linux swap / Solaris
```
In fact, in the Blocks column, it is approximately 1,000,000 per GB, so my sda1 which is 9.9GB shows 10,482,381 blocks.

Yes indeed I can only see two drives (plus the CD-R drive) there.

---

### Post by ajgreeny on 2012-03-17
In that case, and assuming the disk itself still is working, I suspect that you need to play around with the jumpers on it, if there are any and try all combinations until, hopefully, the disk is detected by BIOS and Ubuntu.

---

