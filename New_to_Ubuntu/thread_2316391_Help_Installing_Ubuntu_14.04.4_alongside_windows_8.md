---
title: "Help Installing Ubuntu 14.04.4 alongside windows 8.1"
date: 2016-03-07
forum: New to Ubuntu
---

### Post by aberganza1997 on 2016-03-07
Hello everyone, I'm trying to install Ubuntu 14.04.4 alongside windows 8.1, but when ever I try to install it I don't get the option to install alongside windows. Also, I'm trying to install Ubuntu on my second hdd which is empty. Can someone please help me do this and if I install it on my second hdd will I still get the option to select either windows or Ubuntu on startup? Thanks for your help

---

### Post by oldfred on 2016-03-07
Was Windows pre-installed? So then UEFI?
You mention both 14.04 and 12.04. Best to only use newest versions or 14.04.4 and in two months 16.04 if hardware is newer.

And is second drive gpt partitioned?
And does it have an ESP - efi system partition near beginning of drive. It may not be used during install or even absolutely required if internal drive, but better that every drive is gpt & has its own ESP.

If drive is blank, create your own partitions and use Something Else to install to the partition you want as / (root).

 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

Several threads on two drive installs.

 [http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/)
Uses rEFInd on HP with 2 drives
[http://askubuntu.com/questions/721867/dual-boot-ubuntu-14-04-3-lts-with-win-10-on-separate-hard-drives](http://askubuntu.com/questions/721867/dual-boot-ubuntu-14-04-3-lts-with-win-10-on-separate-hard-drives)
Install Ubuntu in UEFI mode on second HDD without affecting first HDD
[http://ubuntuforums.org/showthread.php?t=2305876](http://ubuntuforums.org/showthread.php?t=2305876)
[http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot](http://askubuntu.com/questions/591193/install-ubuntu-alongside-win-8-1-on-separate-physical-drives-and-dual-boot) 



Also see links in link below in my signature.

---

### Post by aberganza1997 on 2016-03-07
Thanks for the info. I meant 14.04.4 it was a typo and I fixed it. I also followed the steps in the fourth link and disconnected my hdd with windows and installed ubuntu on the other. After I installed it, I connected the other hdd and did sudo update-grub but when I restarted my computer it automatically opens ubuntu.

---

### Post by yancek on 2016-03-07
When you ran sudo update-grub, you should see output of what is found.  Did you see any indication of a windows system?  Usually, windows 8 is installed UEFI. Did you verify that before installing Ubuntu and did you then install Ubuntu UEFI.  Might be best if you haven't resolved the problem, to get the boot repair software and select the option to CREATE BOOTINFO SUMMARY and post a link to the output here as it will have a lot of details needed to help resolve the issue.   

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by aberganza1997 on 2016-03-07
This is what I get when I run the boot repair: GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Here is the link:
[http://paste.ubuntu.com/15324836/](http://paste.ubuntu.com/15324836/)

---

### Post by Bucky Ball on 2016-03-07
Looks like Windows is installed in the older BIOS mode and you have installed Ubuntu in UEFI. That won't work and sure oldfred can give you some clues about fixing it.

You could have avoided this mess (probably) by replying to oldfred's first question and confirming whether Win was installed in UEFI or not:

[QUOTE=oldfred]Was Windows pre-installed? So then UEFI?[/QUOTE]

---

### Post by oldfred on 2016-03-08
Windows was installed in BIOS mode on sda. How you boot install media is how it installs.
And Ubuntu is UEFI boot mode on sdb.

UEFI and BIOS boot modes  are not compatible. But you can dual boot from UEFI or maybe one time boot key.
Some UEFI require you to turn on/off UEFI or CSM/BIOS/Legacy to match system you boot, others recognize how you are booting and will work from one time boot key.

You can reinstall Windows in UEFI mode, or convert Ubuntu to BIOS boot mode.
You can easily convert Ubuntu to BIOS with Boot-Repair's advanced mode. It actually un-installs grub-pc (BIOS) and installs grub-efi-amd64 (UEFI). You must first create a tiny 1 or 2MB unformatted partition with the bios_grub flag if using gparted. That is so grub can install in BIOS mode correctly on gpt partitioned drive.

Grub likes to default to sda so you may have some issues.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

