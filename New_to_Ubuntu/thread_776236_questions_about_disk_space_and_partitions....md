---
title: "questions about disk space and partitions..."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jasperarcher on 2008-04-30
hello all, pardon is requested in advance for what be some very dumb questions, however i have been poking around on my own in this forum and in some other documentation and i can't seem to figure this out. 

 - successful install of ubuntu 8.04 the other day on my toshiba laptop, finally got ride of XP (ew).  

 - had to install from a 4 gig USB stick because the CD-ROM drive on my laptop has physical damage.

 - problem 1: although i have an 80 gig hard drive, i cannot install the moneydance demo because it says i don't have enough disk space.  nor can i transfer photos and mp3's into my "documents" area, for the same reason.  when i right click on my "documents" folder it says i have 5.2 MB free!

 - problem 2: i always have to use the USB to boot up the computer.  if the USB is not in there, and it tries to boot from the HD, it says "GRUB _" and hangs.  however, when i boot from the USB, i choose the option "boot from hard drive" and ubuntu starts up just fine.

here is the result of "sudo fdisk -l"
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7e3f7e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000fe6d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         502     4030432+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 15)

Disk /dev/sdc: 2003 MB, 2003304448 bytes
64 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         970     1955455+   6  FAT16

when i tried "sudo gedit /boot/grub/menu.lst", i got a blank document!

any ideas or pertinent links would be oh so helpful.  i the meantime i'm gonna continue to read up.

best,
jasper archer

---

### Post by Big Luke on 2009-07-28
Im supposed to be writing a paper on the Treaty of Versallies right now but im stalling...so ive skimmed through your post and it seems as if you are having a problem with GRUB, I would download a copy of [Super Grub Disk]("www.supergrubdisk.org")if I were you and try and reinstall GRUB.

I am sorry I cant give you my undivided attention right now but I am trying to make it look like I am typing my paper...Ill look more when I get home...if I remember lol good luck

---

### Post by mapes12 on 2009-07-29
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7e3f7e3

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9541 76638051 83 Linux
/dev/sda2 9542 9729 1510110 5 Extended
/dev/sda5 9542 9729 1510078+ 82 Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000fe6d0

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 502 4030432+ c W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
phys=(500, 254, 63) logical=(501, 196, 15)

Disk /dev/sdc: 2003 MB, 2003304448 bytes
64 heads, 63 sectors/track, 970 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdc1 1 970 1955455+ 6 FAT16 

Some of this looks odd to me:

- The output reports 3 physical disk devices at sda, sdb and sdc
- It looks like windoze is still on the system in some form or other with sdb and sdc being reported as FAT32 and FAT16 partitions respectively
- sda doesn't look as if much room has been allocated for UBU with the partions sda1, sda2 and sda3 looking very small. 

There may be unallocated space on sda. To check I would run GParted (It's in Synaptic. Then System>Administration>Partition Editor - be mindful that you cannot make changes to a disk which is running your system) to have a look at what the GUI reports. Maybe take a screen shot and post here.

---

