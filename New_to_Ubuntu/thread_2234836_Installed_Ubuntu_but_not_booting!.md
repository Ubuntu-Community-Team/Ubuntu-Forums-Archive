---
title: "Installed Ubuntu but not booting!"
date: 2014-07-17
forum: New to Ubuntu
---

### Post by Andreas_Pallidis on 2014-07-17
Hello guys, total newbie here!

So some weeks ago my PC windows totally crashed and cant load windows (7 32bit). When i try to start logging on windows it start making a very time consuming scan that never leads to anything, just the pc freezes.

SO then i made a DVD for ubuntu (btw my pc is unable to boot from USB).After some problems with my partitions i finally managed to install ubuntu 14.04. After installation, the system asked for reboot but the reboot failed. SO the 14.04 ubuntu is installed in my PC but does not boot. 

What can be useful:
-I ran a check of my Hard drive (from ubuntu boot DVD) and my drives seem ok
-In my BIOS setup i cant see the ubuntu boot file.
-I already downloaded and installed Boot repair, but my boot seems ok. Here is the report: [http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

All help is very valuable.

Cheers

---

### Post by Bashing-om on 2014-07-17
Andreas_Pallidis; Hi ! Welcome to the forum.

Your paste link returns " paste not found". Please try again.
We will get to the bottom of things and get you up and running 

[INDENT]ubuntu, our
[INDENT][INDENT][INDENT]operating system by choice
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Andreas_Pallidis on 2014-07-17
[http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

Sorry!

---

### Post by Andreas_Pallidis on 2014-07-17
Sorry for my broken links! i updated them so u can check!

---

### Post by Bashing-om on 2014-07-17
Andreas_Pallidis; Uhmp,

Prospects for the 1st hard drive 'sda' do not look good to me.
I am not conversant with Windows to the extent to advise as I see linux , 'sda7' installed within a Windows extended partition and it appears that boot-repair does not detect any bootloader installed to the MBR of the hard drive.

Others will have to advise as I do not know the effects of running Windows file system check/repair on a hard drive that also contains the ubuntu operating system.

I will be interested to see what those who do know advise.

[INDENT][INDENT][INDENT]the process of learning
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-07-17
It seems to have an issue with the drive.
And it is always best to shrink Windows using Windows own tools. You had to shrink Windows from the installer or gparted when Windows already was broken which may make it impossible or extremely difficult to fix.

Post this, but I expect it to be the same as the script.

sudo parted -l
sudo fdisk -lu

---

### Post by Andreas_Pallidis on 2014-07-17
sudo parted -l 
gives these results:

Error: /dev/sda: unrecognised disk label 

(the rest are for my externally (usb) added drive)

sudo fdisk -lu 
gives these results:
Disk /dev/sdg: 320.1 GB, 320072843264 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x107b0616

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63   625137344   312568641    c  W95 FAT32 (LBA)

---

### Post by Andreas_Pallidis on 2014-07-17
I am pretty fine with uninstalling the current ubuntu and reinstalling them.But when i do i get the error message "input/output error read on /dev/sda".
What i read from other posts said to change my drive from SATA to AHCI, but when i go to BIOS the only option i have is to RAID. THats what i did and then the installation continued (with some error messages, but i pressed ignore).

---

### Post by at_first_light on 2014-07-17
It seems to be complaining about are sda having an invalid mbr signature, no bootloader being detected on it, and not being allowed write access on sda or sda7.

> Invalid MBR Signature found
- Source: [http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

> 
=> No known boot loader is installed in the MBR of /dev/sda.
- Source: [http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

> sda7 is Read-only or full
- Source: [http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

> 
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 7 boot on

                                                                          
Warning: Error fsyncing/closing /dev/sda: Input/output error

                                                                          
Error: Input/output error during write on /dev/sda

                                                                          
Warning: Error fsyncing/closing /dev/sda: Input/output error


- Source: [http://paste.ubuntu.com/7806316/](http://paste.ubuntu.com/7806316/)

Your signature looks to me like it ends in "0x 55 AA" as it should, so I'm not sure what the problem there would be? The bootloader likely doesn't exist because the system won't allow it write access. This can't be due to read only access as I would assume it's not a read only drive :P , nor can it be a space issue because it's listed as having free space on all 3 partitions with 42G of free space on the OS partition sda7. 

I'm not sure what the problem is. You could have a look at drive sda using Gparted to see if it lists any problems on it (with a ! mark that you can click on for more information). Gparted is already installed on the livecd.

---

### Post by oldfred on 2014-07-17
Also lets see what this shows:

 sudo blkid -c /dev/null -o list

---

### Post by oldfred on 2014-07-17
Also lets see what this shows:

 sudo blkid -c /dev/null -o list

---

### Post by Andreas_Pallidis on 2014-07-18
sudo blkid -c /dev/null -o list

/dev/loop0 squashfs         /rofs          
/dev/sda1  ntfs    Windows  (not mounted)  5604A23B04A21DCD
/dev/sda5  ntfs    Programs (not mounted)  ECB8A5C1B8A58B22
/dev/sda6  ntfs    Personal Files (not mounted) 06BEE054BEE03DB5
/dev/sda7  ext4             (not mounted)  c3069e91-3989-4203-81d1-927710a852b5
/dev/sda8  swap             <swap>         493da899-76ab-4c60-a2a7-dd9802f3f9a4
/dev/sr0   iso9660 Ubuntu 14.04 LTS amd64 /cdrom

---

### Post by oldfred on 2014-07-18
Partition list from blkid looks normal?
The partition labels seem ok, so I do not know what a drive label error is?

Post this also:
sudo hdparm -I /dev/sda

Does Disks or Disk Utility show drive and partitions?

---

