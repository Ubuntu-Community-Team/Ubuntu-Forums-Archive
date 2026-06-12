---
title: "How do I format an unallocated partition?"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by Rachel_Bunker on 2014-01-10
In November (around Thanksgiving) I got a new laptop.  I currently have both Windows 7 and Ubuntu 13.10 installed on it.  I'm not sure if it's a true dual boot because I have Windows on the HDD and Ubuntu on the SSD.  Anyway, during the installation process I shrunk the windows partition and now I have 222.65 GB of unallocated space on the HDD.  I would like to format this space into a partition for Ubuntu to use for storage but I don't know how to go about doing so.  Any help would be greatly appreciated!

---

### Post by oldos2er on 2014-01-10
Install gparted ```
sudo apt-get update && sudo apt-get install gparted
``` In gparted, right-click on the unallocated space and choose 'New....'

---

### Post by jdeca57 on 2014-01-10
I started to write an answer but then I thought that this must be answered on the net.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
use gparted like mentionned on the free part of the disk note the partition number and make an entry in /etc/fstab

---

### Post by Rachel_Bunker on 2014-01-11
I'm having a problem with Gparted.  It won't work.

---

### Post by Iowan on 2014-01-11
Can you be more specific? 
Won't start?

---

### Post by nilla78ro on 2014-01-11
try command line:
 [COLOR=#000000][FONT=Ubuntu Mono]mkfs.ext4 -L <label_name> <device>[/FONT][/COLOR]

---

### Post by Mark Phelps on 2014-01-11
>  during the installation process I shrunk the windows partition and now I have 222.65 GB of unallocated space on the HDD.

HOW did you do this? Using the Ubuntu installer?  IF so, you need to boot into Win7 to ensure it still boots -- as shrinking the Win7 OS partition with the Ubuntu installer can sometimes result in Windows filesystem corruption.

Once there, if Win7 does boot OK, then you can use the Win7 Disk Management tool to create a new NTFS partition in the unallocated space.

---

### Post by oldfred on 2014-01-11
Have you used all 4 primary partitions on hard drive?
May be best to see current partitions:

sudo parted -l

---

### Post by Rachel_Bunker on 2014-01-11
I did the sudo parted -l and only 3 partitions are there.

I have successfully booted Windows several times.

The way I shrunk the Windows partition was in Windows itself using the disk management utility.

What I mean by gparted won't work is that it keeps searching /dev/sda partitions and it basically stops there.  I mean, the bar thing keeps going back and forth but nothing else happens.  I can't even access the menus.

---

### Post by oldfred on 2014-01-11
That often happens when it cannot mount Windows or another partition. Did you reboot Windows after resize so it can run chkdsk? And is Windows hibernated.
Also if it was Windows 8 and you converted to Windows 7 did you also convert to BIOS/MBR from UEFI/gpt? If so you may have left over gpt backup partition table. Windows does not convert to MBR correctly.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Rachel_Bunker on 2014-01-11
I've rebooted Windows several times after resize.  The computer came with Windows 7 so the BIOS/MBR thing is not an issue.

---

### Post by Dave_L on 2014-01-11
> **Rachel_Bunker said:**
> I did the sudo parted -l and only 3 partitions are there.

I have successfully booted Windows several times.

The way I shrunk the Windows partition was in Windows itself using the disk management utility.

What I mean by gparted won't work is that it keeps searching /dev/sda partitions and it basically stops there.  I mean, the bar thing keeps going back and forth but nothing else happens.  I can't even access the menus.

Can you post the output from "sudo parted -l"?

Do you know how to run "fsck"? Maybe there's something about the existing partitioning that gparted doesn't like and a disk check would provide a clue.

---

### Post by Rachel_Bunker on 2014-01-13
First, I want to apologize for taking so long to respond.  I took a small vacation and did not take my computer with me.

Anyway, here's the output from sudo parted -l
```
Model: ATA Hitachi HTS72755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  13.2GB  13.2GB  primary  ntfs         boot
 3      13.2GB  261GB   248GB   primary  ntfs




Model: ATA SAMSUNG SSD PM83 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  27.9GB  27.9GB  primary   ext4            boot
 2      27.9GB  32.0GB  4094MB  extended
 5      27.9GB  32.0GB  4094MB  logical   linux-swap(v1)

```
As for fsck, I do not know how to run that.

---

### Post by ppjdee on 2014-01-13
I personally would use a windows install cd to edit the partition. Using jelly bean to save a .txt file of all my reg keys to be on the safe side, isnt a bad idea either.

---

### Post by Dave_L on 2014-01-13
> What I mean by gparted won't work is that it keeps searching /dev/sda partitions and it basically stops there. I mean, the bar thing keeps going back and forth but nothing else happens. I can't even access the menus.

I found some posts that describe the same symptom as yours (gparted hangs), with suggested fixes:

[https://www.linuxquestions.org/questions/debian-26/gparted-just-hangs-and-i-don%27t-know-why-502353/](https://www.linuxquestions.org/questions/debian-26/gparted-just-hangs-and-i-don%27t-know-why-502353/)

[http://gparted-forum.surf4.info/viewtopic.php?id=16547](http://gparted-forum.surf4.info/viewtopic.php?id=16547)

[http://www.pclinuxos.com/forum/index.php?topic=110345.0](http://www.pclinuxos.com/forum/index.php?topic=110345.0)

---

### Post by oldfred on 2014-01-13
Is this an UltraBook? With the small SSD. 
That uses Intel SRT which has RAID and the desktop installer does not work with RAID, plus it is not a standard RAID for a server install anyway.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

