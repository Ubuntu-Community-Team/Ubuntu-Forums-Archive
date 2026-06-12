---
title: "Dual boot/2 drives Ubuntu, Vista"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by ray9 on 2015-01-22
So I have Ubuntu 14.04LTS on one drive and Vista on the other.  The other day Vista wanted to install SP2 and that was the end of Vista, SP2 failed to install and went into the "loop".  I tried everything I could find to fix it but was unable to do so I reinstalled.  But while looking for a solution I read where GRUB could cause SP2 from failing to install, something about the restart.  If this was the case how can I install SP2 w/o GRUB causing a failure?  I was thinking that I could put SP2 on a CD, unlug the Ubuntu drive and install it that way but I don't know how I would get Vista to boot.  Any ideas?

---

### Post by oldfred on 2015-01-22
Is Vista totally on one drive?
If so just disconnect the Ubuntu drive and run it as a Windows only system.

Grub really only boots working Windows and best configuration with two drives is that each drive works without the other. 
Windows should be able to have its boot loader in the MBR of the Windows drive and grub boot loader installed to the MBR of the Ubuntu drive.

Post this from Ubuntu or Ubuntu live installer:
sudo parted -l
sudo fdisk -lu

---

### Post by ray9 on 2015-01-22
Yes, each has it's own drive, married together with "boot repair".

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009b9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   186032127    93015040   83  Linux
/dev/sda2       186034149   976771071   395368461+   5  Extended

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d726e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   148441087    74219520    7  HPFS/NTFS/exFAT
/dev/sdb2       148443134   156301311     3929089    5  Extended

---

### Post by fantab on 2015-01-23
You can repair the Vista boot with [fix MBR]("http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/"). Then update to SP2, it should work.
You may have to set the Windows HDD as first boot in BIOS.

You will have to [Reinstall Grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"). Boot-repair installs grub in the MBR of both HDDs.
I wouldn't want grub on Windows HDD, its a good idea to keep Win bootloader on its own HDD.
So use the method described in the 'reinstall-grub' link and install grub to /dev/sda, which, by the way, is also the default location of the HDD.

In BIOS reset the boot order to boot Ubuntu first, if you have changed it earlier.

Also its a good thing to have a SWAP partition in Ubuntu HDD.

---

### Post by Derrick_Katula on 2015-01-23
use ubuntu from a flash disk & windows from the hard drive

---

### Post by ray9 on 2015-01-23
Thanks for the replies!

---

