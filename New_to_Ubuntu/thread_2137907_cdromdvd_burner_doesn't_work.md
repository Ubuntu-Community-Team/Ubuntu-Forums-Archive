---
title: "cdrom/dvd burner doesn't work"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by danewshaboo on 2013-04-22
Hello

I used to have windows 7 after a serious virus I wiped my partition clean and installed Debian GNU/linux 7.0. Have been reading post in your forum and still haven't resolved problem. I don't know if the driver needs needs to be reinstalled, I haven't been abled to create a mount point. Anyway this is what I get when in terminal; 

 **sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1     2104514     1052257   82  Linux swap / Solaris
/dev/sda2   *     2104515   312576704   155236095   83  Linux

**and this: **

knoppix@Microknoppix:~$ sudo  /usr/sbin/hwinfo --cdrom
23: SCSI 400.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_serial_HL_DT_STCD_RW_DVD_DRIVE_GCC_4247N
  Unique ID: KD9E.5sKIYAwAU+E
  Parent ID: 3p2J.RgjU6vCo3M6
  SysFS ID: /class/block/sr0
  SysFS BusID: 4:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/ata5/host4/target4:0:0/4:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST RW/DVD GCC-4247N"
  Vendor: "HL-DT-ST"
  Device: "RW/DVD GCC-4247N"
  Revision: "1.02"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/disk/by-id/ata-HL-DT-STCD-RW_DVD_DRIVE_GCC-4247N, /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (IDE interface)
  Drive Speed: 24
do you understand this stuff ? I don't.:confused:

---

### Post by BBQdave on 2013-04-22
> **danewshaboo said:**
> ...and installed Debian GNU/linux 7.0.

Making some assumptions... If you have Gnome 3 with Debian 7 *testing*, you should be able to access CD-DVD media through Nautilus, Brasero, or possibly the bottom bar of your desktop. If you are having difficulties burning disks, I would suggest Xfburn instead of Brasero.

Debian 7 is testing, if you have a chance to test with a Live CD - you could try Ubuntu.

---

### Post by gordintoronto on 2013-04-22
What do you want to do? What is happening instead? "Doesn't work" provides no clues people might use to help you.

---

