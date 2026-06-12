---
title: "System can't detect HDD"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by fernetekhd on 2013-04-07
So my PC has two drives: a SSD (where Ubuntu is installed) and a HDD (where nothing is installed, and where I want the majority of my programs to install). 

However, even though my Bios detects (it's in the boot order and everything, and on one install attempt for Ubuntu it was the main drive) the HDD, Ubuntu will not (it DOES detect, for example, the USB stick that has the Ubuntu ISO on it).

So I need some help here. I did find a thread from about ~2010 (similar problem but different solution) that listed some commands y'all might need me to run from the terminal, so here're they're outputs:

**sudo fdisk -l**

Disk /dev/sda: 60.0 GB, 60022480896 bytes **(<---- SSD is 60 GB, HDD should show as 320 GB)**
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015422


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   100493311    50245632   83  Linux
/dev/sda2       100495358   117229567     8367105    5  Extended
/dev/sda5       100495360   117229567     8367104   82  Linux swap / Solaris


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc: 16.0 GB, 16043212800 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31334400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0516b45b


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    31334399    15666176    c  W95 FAT32 (LBA)
rob@rob-MS-7750:~$
[B]



dmesg | tail -n 20

[/B][    3.037461] scsi 7:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    3.038067] scsi 7:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    3.038678] scsi 7:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    3.039302] scsi 7:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    3.039752] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    3.039875] sd 7:0:0:1: Attached scsi generic sg5 type 0
[    3.041146] sd 7:0:0:2: Attached scsi generic sg6 type 0
[    3.042831] sd 7:0:0:3: Attached scsi generic sg7 type 0
[    3.062024] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[    3.062775] sd 7:0:0:1: [sde] Attached SCSI removable disk
[    3.063524] sd 7:0:0:2: [sdf] Attached SCSI removable disk
[    3.064148] sd 7:0:0:3: [sdg] Attached SCSI removable disk
[    3.100584] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    3.100652] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    3.100722] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    3.100829] input: 
[B]
P.S. Both drives were boot n' nuked ~an hour before I installed Ubuntu. Also, I'm pretty sure both drives have a NTFS format (could be wrong though).
P.P.S. <---- Complete nub at Ubuntu.[/B]

---

### Post by sanderj on 2013-04-07
/dev/sdb is your HDD:

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
Disk /dev/sdb doesn't contain a valid partition table

Do you want to create a partition? If so, hit "Super"-key (with Windows logo), type "disks", and click on "Disks". Does that show /dev/sdb on the left ... ?

---

### Post by fernetekhd on 2013-04-07
It does! So what do I do with it?

---

### Post by sanderj on 2013-04-07
Just checking: Disks also says there is no partition. If so, there is no information, so you can loose anything.

On the left, select /dev/sdb.
Then, on the right, select the two wheels. It will offert to create a partition (do that) and to format it (do that too). Then mount it.

---

### Post by fernetekhd on 2013-04-07
It worked! Thanks!

---

