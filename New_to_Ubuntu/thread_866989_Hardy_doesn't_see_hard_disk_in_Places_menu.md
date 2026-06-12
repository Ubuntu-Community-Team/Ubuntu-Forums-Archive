---
title: "Hardy doesn't see hard disk in Places menu"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Chemroydal Tissue on 2008-07-22
I recently upgraded from Gutsy to Hardy. However, I only had one of two backup hard disks mounted (one, a 500GB SATA disk, was mounted. The other, a 200GB ATA disk, was not) during the upgrade. Now, only the 500GB drive shows up in the Places menu, which is where I would like both drives to be displayed. I suppose I could just mount the drive using the Terminal and/or modify /etc/fstab to mount the drive on startup, but I really liked the drives' original location (in the menu) and its functionality.

In case it helps, I've included the results of ```
lshw -C disk
``` pasted below:

>   *-disk                  
       description: ATA Disk
       product: WDC WD2000JB-00G
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WCALL1053461
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=dbb66ddb
  *-cdrom
       description: DVD writer
       product: DVDR   PX-740A
       vendor: PLEXTOR
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Ubuntu 7.10 amd64
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/Ubuntu 7.10 amd64
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk:0
       description: ATA Disk
       product: WDC WD740ADFD-00
       vendor: Western Digital
       physical id: 0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdb
       version: 20.0
       serial: WD-WMANS1155812
       size: 69GiB (74GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000437fb
  *-disk:1
       description: ATA Disk
       product: ST3500641AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@9:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       serial: 3PM0WHSG
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e7cc6


---

### Post by cprofitt on 2008-07-22
Two things cross my mind...

The 200gb is not formatted - install gparted and partition it.

If it is formatted can you manually mount the disk?

---

### Post by Chemroydal Tissue on 2008-07-22
-Yes

-I haven't tried, but I assume so. I am at work.

---

