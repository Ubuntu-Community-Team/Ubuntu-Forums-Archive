---
title: "Grub Windows and Boot-Repair"
date: 2018-05-25
forum: New to Ubuntu
---

### Post by iioiooioo on 2018-05-25
Hello! I'm currently trying to get my dual-boot Windows and Ubuntu 18 system operational again. I'm trying to follow the instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I attempted the "Recommended Repair", which has worked for me in the past, but Windows does not show up in the boot options. I am now on to the next step of hoping someone can assist me with the correct BootRepair options. The generated pastebin is at [http://paste.ubuntu.com/p/9sdHj3zrcr/](http://paste.ubuntu.com/p/9sdHj3zrcr/).

This was all working well until I reinstalled my Ubuntu system, using the default options. I've also done this in the past, but this time it caused the Windows boot option to disappear from the Grub boot menu. If it helps, I believe sda is the correct Windows disk, and sdc is the correct Ubuntu disk. None of the drives were or should be RAID.

Thank you for your assistance, I am somewhat new to Ubuntu in general and very new to Grub configuration - in the past this has all just worked automatically.

---

### Post by oldfred on 2018-05-25
UEFI & BIOS boot modes are not compatible. They write hardware info onto drive for operating system differently.
You can then only dual boot from UEFI boot menu and may have to turn on/off UEFI or BIOS boot modes to match install.

You have Windows BIOS boot on sda with MBR partitioning.
You have an UEFI boot on sdc, using the advanced LVM - logical volume management system. 

Line 1334, you have Windows dynamic partitions which is something like LVM. Best not to use LVM as not compatible with Linux as it is proprietary to Microsoft.
> SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.

Best to just install Windows boot loader to sda and keep grub only on Linux drive, sdc.
Do not run autofix with Boot-Repair, but use only advanced mode.

Windows 10 also turns on fast startup or hibernation with updates, so you may need to turn that off again after Windows update.

---

### Post by iioiooioo on 2018-05-26
Thanks for the advice, @oldfred. It sounds like I may have messed this all up even worse than I first thought. It is less than ideal to "only dual boot from UEFI boot menu and may have to turn on/off UEFI or BIOS boot modes to match install".

I read through the link at the bottom of your post. It sounds like the part where I went wrong was to choose LVM during Ubuntu reinstall. The reason I was reinstalling was due to partition resizing difficulties, so I hoped to potentially alleviate future issues by using LVM (it said something about making partition resizing easier, I think). 

As I do not have a lot of time invested in the current Ubuntu installation, I wonder if I would be better off simply reinstalling Ubuntu correctly (or "Converting Ubuntu into Legacy mode" from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)). Based on "Do not use LVM nor full drive encryption if new user. It will erase your Windows and requires advanced knowledge.", from your link, I'm not even sure this would help. I'm also not sure about whether I should try "converting Windows dynamic partitioning (SFS partitions) to a basic disk", regardless of the method I use to solve this. 

I would really love to go back to as close to I can get to my previous configuration (or whatever the ideal configuration is), which allowed simple selection during boot and crazy fast boot times for both OSes.

Thanks again for you help so far, hopefully this isn't too many questions, I'm really trying to understand how this all goes together.

---

### Post by oldfred on 2018-05-26
Since your LVM is on a separate drive, you can keep it. Often users see that easier partitioning and install LVM on the same drive as Window which then erases Windows and everything else on that one drive.
You probably can convert to BIOS boot, if desired. Shrink your ESP by several MB and add a tiny 1 or 2MB unformatted partition with the bios_grub flag. Then use Boot-Repair booted in BIOS mode, make sure it has mounted your LVM so it sees / (root) (it should, but sometimes users with encrypted LVM do not mount it and then have issues). And then use Boot-Repair to do a full uninstall/reinstall of grub2. It will uninstall the UEFI version of grub and install the BIOS boot version of grub. If you keep ESP, you later can convert drive to UEFI boot again, when you decide to install Windows in UEFI boot mode.

Those that use LVM seem to like it, it does allow easier partitioning but only using LVM tools inside the LVM, gparted does not work on LVM. Only on the physical partition container which you almost never resize and the LVM is fully using the partition.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 
    
It looks like your  sdb is the SFS drive. I would convert it. Not sure how it would become dynamic partitions. I thought Windows only wanted to convert to dynamic partitions when you used more than the 4 primary partitions used with MBR(msdos) partitioning. Is there something unique about drive?
Be sure to have good back up of sdb data. It also looks like it has issues with start sector. Older partitioning with XP used 63 as first sector. Windows 7 started using 2048 for compatibility with newer 4K drives and SSDs. Since sdb is an SSD, it needs start sector of 2048.

I suggest using gpt on any drive, that is not BIOS boot of Windows as Windows in BIOS boot mode does require MBR. Or any data only or Linux only drive. Windows 7 or later in BIOS mode still reads gpt partitioned drive without issues as long as partition(s) is NTFS.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

If you have lots of effort in configuring your system, you need good backups. Desktops have almost everything in /home. Servers or server type software like web, database etc may have data in / (root).
       
 Gui tool:
[http://www.teejeetech.in/p/aptik.html](http://www.teejeetech.in/p/aptik.html)
discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
      [/URL]
 Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810) 
    

I use rsync & copy data to multiple places, several drives & flash drives. Most critical data ( mostly grandkids photos) also are copied to DVDs.
[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

---

### Post by iioiooioo on 2018-06-02
Thanks, again, @oldfred. Your help enabled me to get everything back up and running again (and I learned a lot in the process). I appreciate it.

---

