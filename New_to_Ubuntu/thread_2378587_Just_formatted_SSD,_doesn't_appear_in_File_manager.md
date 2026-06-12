---
title: "Just formatted SSD, doesn't appear in File manager"
date: 2017-11-24
forum: New to Ubuntu
---

### Post by sterator on 2017-11-24
Is it normal for a disk to not appear in the file manager windows after it's formatted? Is there something I can do to make it re-appear?

thank you!

---

### Post by yancek on 2017-11-24
How did you format the disk and what filesystem did you use?
Did it previously contain a filesystem in some format?
Is there anything on the disk?
Have you mounted the disk partition or re-booted?

---

### Post by sterator on 2017-11-25
Thank you.

I used "Disks" and chose "Format Disk" from the pulldown menu.

The disk contained no filesystem other than as a backup.

I believe that there is nothing now on the disk but I can't confirm because I can't see the disk. In "Disks" it says the disk is "OK" and has 500GB of space..it's a 500GB SSD.

I have rebooted, but am unable to mount the disc.

At least "Disks" is aware of it.

---

### Post by oldfred on 2017-11-25
You do not mount disk, but partitions, so if you erased the drive there is nothing to mount.

If newer system better to use gpt partitioning over the 35 year old MBR(msdos) partitioning.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[/URL]
 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt

Some using Disks have had issues, generally better to use gparted, parted, or gdisk.
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by sterator on 2017-11-25
so, did I render that SSD damage/useless/invisible to my computer by formatting with Disks?

---

### Post by sterator on 2017-11-25
looking at both drives under gparted, it's a bit confusing...the one that says it has 507MiB unused, says mount point is /boot/efi, file system fat32

the one shown to have no unused space says mount point ubuntu-vg..it's file system lvm2 px


how does one know which is which?

---

### Post by Holger_Gehrke on 2017-11-25
I think you're looking at the wrong device - the one with your EFI boot partition and your root partition on it. There's a drop down menu at the right side of the toolbar in the gparted window. You can select the device to work on with that. Unless you've got some additional devices connected, you should have only two devices to choose from there.

Holger

---

### Post by oldfred on 2017-11-25
You should not use gparted or regular partition tools on LVM or LVM with encryption drives.
The LVM partitions require LVM tools. All standard tools will show with LVM is the ESP (If UEFI), /boot partition and one very large partition that contains all the LVM partitions you have.

LVM is an advanced partitioning system, but is used with full drive encryption. 
Default install erases an entire physical hard drive and uses all of it.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by sterator on 2017-11-25
the drop down shows /dev/sda and /dev/sdb, both 465.76 GiB

clearly I'm at a deficit as to what to do and how to do it properly!

when I first installed this 2nd SSD and fired up the machine, I simply appeared..I'm not sure whether the system offered of its own to format it for linux, but if it had, I would have chosen the option that was for linux-compatible systems.

---

### Post by yancek on 2017-11-25
Try opening a terminal and entering the following command and posting the output here for starters:

```
sudo parted -l
```

That's a lower case Letter L in the command.  It will show both drives and their partitions.

---

### Post by sterator on 2017-11-25
> **yancek said:**
> Try opening a terminal and entering the following command and posting the output here for starters:

```
sudo parted -l
```

That's a lower case Letter L in the command.  It will show both drives and their partitions.


Thank you..here is the result:

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot, esp
 2      538MB   500GB  500GB                     lvm


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  17.2GB  17.2GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 482GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  482GB  482GB  ext4

---

### Post by oldfred on 2017-11-25
Your sda looks like a LVM type install.
But if UEFI, you should have both an ESP - efi system partition as FAT32 with boot flag and a separate /boot partition as ext4. Then the main partition which contains the LVM.

You second drive says loop.
That is typically what the hybrid DVD/flash drive installer makes on flash drives.
Did you use dd or a Linux installer to create an install disk on your sdb, not on a flash drive or DVD?

---

### Post by sterator on 2017-11-25
Before I had the 2nd SSD (slated for backup duty) I'd made an Ubuntu installer on a 16-GB USB thumb drive...this is what I used to install Ubuntu onto SSD #1

There were no issues, except that I wasn't 100% sure about some of the initial choices one must make..I'd been posting questions here and there, and I must have made the right selections, because I ended up with an installation of Ubuntu that worked.

Couple of months later, I bought another SSD, attached it to the sled an put 'er in..powered up the machine and there it was.

I'd had trouble getting "Backups" to work, so I bailed on that and went with grsync, which worked with only sporadic permissions issues until the other day.

The machine in question is a 2009 "nehalem" Mac Pro, single boot Linux, 16GB ram.

I also have a Mac Book Pro, dual-boot Ubuntu and OS X.

---

### Post by Geoffrey_Arndt on 2017-11-26
This is one reason I recommend "relatively" inexperienced users do not select LVM during an initial install.  Just adds unneeded complexity and reduces chances of quick online help.

---

### Post by sterator on 2017-11-26
I'm getting the feeling that, way back when I installed Ubuntu on this machine, that I made a choice that now puts me in a bad position regarding formatting discs..

Which baffles me..so..the installer and or a tool installed with Ubuntu would...let me format a disc in a way that the system can't see or use.

..why would a system "let" one do that? Can this system which I now have, let me re-format a disc which it can now partially "see" to a format which it can see and use and which is compatible with the formatting which it itself now is?

Is there a way out, or is this a lobster trap?

;-)

---

### Post by Holger_Gehrke on 2017-11-26
@oldfred: There's something missing at the beginning of sterator's dump of the output of 'parted -l'. It begins with a partition list instead of the description of the drive that partition table is on. Looks like the table for /dev/sda, and it does indeed have an esp at the beginning.

@sterator: when doing copy and paste from the terminal, I always start at the end of the output and work up. That way I can move into the output that has scrolled out of the window until I can see the command that produced the output and can capture all of it.

Holger

---

### Post by sterator on 2017-11-26
> **Holger_Gehrke said:**
> 

@sterator: when doing copy and paste from the terminal, I always start at the end of the output and work up. That way I can move into the output that has scrolled out of the window until I can see the command that produced the output and can capture all of it.

Holger

My bad..here's the full output:

maker@bento:~$ sudo parted -l
[sudo] password for maker: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot, esp
 2      538MB   500GB  500GB                     lvm


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  17.2GB  17.2GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 482GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 
```

Number  Start  End    Size   File system  Flags
 1      0.00B  482GB  482GB  ext4
```


maker@bento:~$

---

### Post by vasa1 on 2017-11-26
See how using code tags makes terminal output more intelligible. Please use code tags.

---

### Post by sterator on 2017-11-26
Like this?

```
maker@bento:~$ sudo parted -l
[sudo] password for maker: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot, esp
 2      538MB   500GB  500GB                     lvm


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  17.2GB  17.2GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 482GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  482GB  482GB  ext4


maker@bento:~$ ^C
maker@bento:~$ 

```

---

### Post by vasa1 on 2017-11-26
Thanks :)

---

### Post by oldfred on 2017-11-26
I have not seen a LVM install from Ubuntu without a separate /boot partition. But have seen one or two users that have done that manually. Those with UEFI have both the ESP & /boot.

The LVM install says easier partitioning. What it does not really say is that it is full drive and really easier for advanced users. You can actually change partitions when booted into system which is one of its main advantages. But you have to use LVM tools, and most of the advanced users that understand LVM are in the server sub-forum where on a server it does make more sense to use LVM.
But if you want full drive encryption, you also get LVM.

If not really knowledgeable on LVM and its differences from standard partitioning, probably best to back up /home, installed applications and any system file in /etc you manually edited, like grub, exports (NFS), grub's 40_custom etc. I only edit those files & just make a copy into /home when editing so my backup of /home includes those files.

Then you can reinstall.
If very new user you only need / (root) & swap. And with 17.04 and later, swap is now a file. But if swap partition found it will use it. If a bit more advanced, then a separate /home is suggested, but many of us use separate partition(s) just for all data.

 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
If a drive will only have Ubuntu, you can use gpt whether system is UEFI or BIOS, if you have correct supporting partitions. It just is any Windows boot drive must have MBR for BIOS boot and gpt for UEFI boot.

---

### Post by sterator on 2017-11-26
Here's what it sounds like to me:


[LIST=1]
[*]1. the install method I used on this machine put me into a situation which only an advanced user can remedy
[*]Since I am not an advanced user (I actually am not) my option is to back up my files and to re-install Ubuntu
[/LIST]

I have no idea what I would do differently than I did the first time, which led me to this unworkable situation.

I followed the how to make an installer/how to install instructions I found somewhere on this site. There was language along the way to the effect that "this is good for a beginner."

An actual beginner isn't going to know when something is not good for a beginner to do, so to quote Tennessee Williams, beginners rely on the kindness of strangers to get things done in a way that lets them use and manage their Ubuntu install within beginner abilities.

So, I understand, "Back up files, re-install Ubuntu."

I do not see the path that enables me to install Ubuntu that will not put me right back in the spot I'm in now, which seems to be an incorrect selection of file management type.

Is there a beginning-beginner method? A ubuntu for dummies method?  Something that is beginner proof in every sense of that idea?

I am not a beginner at computing, but I do need to be able to follow a procedure which gets me to the place I need to be. I'm a designer/illustrator who wants to use Linux and the software that designers and illustrators use.

Thank you!

---

### Post by Dennis N on 2017-11-26
You can't detect any OSes in lvm partitions with parted*. Instead, run in terminal:

**sudo lvs**

Example from this machine:

```
[11:40 dmn ~]$ sudo lvs
[sudo] password for dmn: 
  LV           VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  korora_gnome os_vg -wi-ao---- 15.00g                                                    
  mint_mate    os_vg -wi-a----- 15.00g                                                    
  mint_xfce    os_vg -wi-a----- 26.72g                                                    
  ubuntu_1710  os_vg -wi-a----- 19.53g                                                    
  umate_1710   os_vg -wi-a----- 26.72g                                            
```

*Sometimes you can't, sometimes you can. See correction to this statement in post 25.

---

### Post by sterator on 2017-11-26
OK..here is the result of my running sudo lvs. Thank you!



```
maker@bento:~$ sudo lvs
[sudo] password for maker: 
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- 449.27g                                                    
  swap_1 ubuntu-vg -wi-ao----  15.99g                                                    
maker@bento:~$ ^C
maker@bento:~$ 

```

---

### Post by Dennis N on 2017-11-26
_Correction_: The statement in post 23 is only partly correct. The lvm volumes ARE detected using parted command in Ubuntu 1710 ( I see your other post even shows them), but NOT detected when I use parted command in Fedora 27 (the latest available).  I just checked them again to be sure. Sorry about that, and it's strange that they should give different output. I was surprised at that.

Looks like you have a good Ubuntu install there?

---

### Post by sterator on 2017-11-26
> **Dennis N said:**
> Looks like you have a good Ubuntu install there?

I'm honestly not sure anymore...here's what I've experienced:

I installed Ubuntu last July and there were no issues during that procedure - no issues that I could tell.

I have been able to copy my files from Mac drives (I'm migrating from OS  X to Linux) without issue..able to open, modify, etc.  

I have been able to do real work, save the work, and when I re-open the file, I could see that my work was saved and I could resume working.

I was able to make grsync backups up until about 4 days ago. inability to back up has halted all of my work on current projects.

I had almost no issues using Ubuntu except that sometimes Ubuntu or File manager would have an error and quit on me. I've seen things like that happen in the early days of OS X.

I installed Cinnamon, then followed a tutorial to adjust it to my liking - I prefer a darker, "professional" interface rather than all of that barking white. I'm not sure that the Cinnamon modification went well - but still the computer functioned.

I'm inexperienced enough that it's unclear what I ought to do, but it's sounding like "back up your files and re-install"

Yet, I don't know how to re-install so that I don't end up right back where I'm at now!

thank you!

---

### Post by Dennis N on 2017-11-26
```
maker@bento:~$ sudo parted -l
[sudo] password for maker: 
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number Start End Size File system Name Flags
1 1049kB 538MB 537MB fat32 boot, esp
2 538MB 500GB 500GB lvm


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number Start End Size File system Name Flags


[COLOR="#FF0000"]Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 17.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number Start End Size File system Flags
1 0.00B 17.2GB 17.2GB linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 482GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 
```[/COLOR]

The stuff at the bottom in red is the details from the sda lvm partition. It is normal output. 'Partition Table: loop' is also normal. You can't see sdb in the file manager because there are no formatted partitions on it. Create at least one partition (ext4) with gparted, and you should be able to mount it from the file manager.

---

### Post by sterator on 2017-11-26
Dennis N;

I believe that I was successful in following your suggestion. I created 2 partitions: the big one not using all of the available space but most of it and it appears in File Manager as "472 GB Volume."

I was hoping to name it, and gparted seemed to allow the new name, but the name isn't changed in file manager..is a reboot needed?

the path appears as this:

/media/maker/0f35f0f7-70ef-414c-82fe-e8f52b0f1e4a


'maker' is my username...'0f35f0f7-70ef-414c-82fe-e8f52b0f1e4a' seems to be what the system views as the name of the partition?


Inching my way back to functionality, thank you!

---

### Post by Dennis N on 2017-11-26
> I was hoping to name it, and gparted seemed to allow the new name, but the name isn't changed in file manager..is a reboot needed?

You need to make a label for the file system. gparted does that too. You can have both a name and a label, but only labels display in the file manager. Names do not.

**Partiton > Label File System**

I'm glad to hear your problem is solved. You can mark it solved with the thread tools.

---

### Post by sterator on 2017-11-26
> **Dennis N said:**
> You need to make a label for the file system. gparted does that too. You can have both a name and a label, but only labels display in the file manager. Names do not.

**Partiton > Label File System**

I'm glad to hear your problem is solved. You can mark it solved with the thread tools.

I was able to change the label successfully and rsync is now in the process of backing up. I ought to know how successful THAT was in about 2 hours, and then after subsequent back ups.

Thank you! This has been quite a good learning experience, but I still probably have some reading to do (links provided by others above).

Formatting a disc in Linux isn't quite the slam-dunk I expected it to be.

8-P

---

### Post by Dennis N on 2017-11-26
Many users have a problem reading and writing to/from a newly installed disk or newly created partition because they have not made themselves the owner to have the necessary permissions.

In case that is a problem:

1. be sure the disk is mounted, then open the terminal.
2. run the command **sudo chown -R maker:maker /media/maker/<disk-label-here>**

Then you have all access permissions.

---

