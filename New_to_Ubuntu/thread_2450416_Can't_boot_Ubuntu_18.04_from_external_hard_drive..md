---
title: "Can't boot Ubuntu 18.04 from external hard drive."
date: 2020-09-13
forum: New to Ubuntu
---

### Post by asaravanos on 2020-09-13
Hi guys, I am completely new to Ubuntu. I am having a problem booting Ubuntu 18.04 from my external hard drive, and I would really appreciate your help if possible. I have already checked a lot of threads similar to my problem but none of these worked for me - or at least I was not able to make them work - so this is why I decided to write my own thread. 

So, here is my situation:

My laptop is Hp EliteBook 840 G1 and has Windows 7 Professional Edition 64-bit on it. In the beginning, I tried to install Ubuntu on my laptop's HDD, but because the disk is dynamic would not let me install Ubuntu on it.

So I decided to go for installing Ubuntu on my Seagate Portable 2TB External Hard Drive Portable HDD. I formatted the disk to NTFS (it would not let me shrink it while it was exFAT), made a 40 GB unallocated space, and then began the installation of Ubuntu. I gave 8 GB to swap space, 32 GB to ext4 and the installation seemed to be successful. After the installation was completed, it asked me to restart my computer. So I did and this was the last time I saw my installed Ubuntu. 

While my laptop boots, I go to Boot Device Options and select the external hard drive, but it just sends me back to the HP screen which is the first thing that appears when my laptop boots. If I don't to anything, it just boots Windows of course. (Also if I boot the USB I used to install Ubuntu, I can get to the "Try Ubuntu" screen).

I changed the BIOS boot order and put the external hard drive first, but this just puts my laptop in a loop appearing the initial HP screen again and again.

I was now trying the boot repair, but this message appeared: 

"SFS detected.
You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk.
This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.
Do you want to continue?"[FONT=arial][SIZE=1][SIZE=3][COLOR=#535A60]
[/COLOR][/SIZE][/SIZE][/FONT]
So, basically I am stuck with not knowing if it would be safe to proceed with this. I have read some other articles but didn't get a clear answer.

I really feel that my problem is not that complicated and that I am probably missing something, but I am completely new to Ubuntu, so I would really appreciate your help.

Please let me know what other additional information you need in order to help me, and I will provide it here.

Thank you very much in advance!

Augustine [FONT=arial][SIZE=1][SIZE=3][COLOR=#535A60]

[/COLOR][/SIZE][/SIZE][/FONT]

---

### Post by sudodus on 2020-09-13
Windows dynamic partitions do not work with Linux.

- If you have a lot of unique data on this disk, it is better to get a new drive for Ubuntu, and ***not*** let Windows do any partitioning. An SSD is a better alternative than a new HDD because it is faster.

- If there is a backup of the data on the disk (on some other drive or at a web cloud service), you can create a new partition table   and partitions when running Ubuntu live from a USB pendrive or DVD disk, with [FONT=Courier New]**gparted**[/FONT] or let the [FONT=Courier New]**Ubuntu installer**[/FONT] do the partitioning during the installation. It can be a good idea to create an extra [FONT=Courier New]**data**[/FONT] partition with the file system NTFS. Such a partition will be available from Ubuntu as well as Windows.

---

### Post by asaravanos on 2020-09-13
sudodus, thank you very much for your reply.

You are talking about the external disk, right? So the fact that I have a windows dynamic partitioning on my laptop's drive, also affects the partitioning of the external hard drive?! I was not aware of that.

So what you are suggesting at the 2nd option is: to 1) Format the external hard drive (and also delete volume so that it becomes unallocated space?) (also does it make any difference if I do these in Windows or in Ubuntu?) . 2) Then create a partition table for my external drive during my new Ubuntu installation or with gparted. And not do any partitioning stuff through Windows, as I did in my case.

I didn't quite catch the last part about the extra partition which would be available from both Ubuntu and Windows. Could you elaborate on this?

Thank you again! Sorry for my many questions

---

### Post by sudodus on 2020-09-13
> **asaravanos said:**
> sudodus, thank you very much for your reply.

You are talking about the external disk, right? So the fact that I have a windows dynamic partitioning on my laptop's drive, also affects the partitioning of the external hard drive?! I was not aware of that.

No I misunderstood. The partition table on one disk does ***not*** affect the other disks.
> 
So what you are suggesting at the 2nd option is: to 1) Format the external hard drive (and also delete volume so that it becomes unallocated space?)

Yes, and you do this from Linux.
> 
(also does it make any difference if I do these in Windows or in Ubuntu?) .

Do this from Linux, maybe easiest when running Ubuntu live from a USB pendrive or DVD disk, with gparted or let the Ubuntu installer do the partitioning during the installation. This way you get a suitable partition table (that works with Ubuntu and Windows).
> 
2) Then create a partition table for my external drive during my new Ubuntu installation or with gparted. And not do any partitioning stuff through Windows, as I did in my case.

Right.
> 
I didn't quite catch the last part about the extra partition which would be available from both Ubuntu and Windows. Could you elaborate on this?

Thank you again! Sorry for my many questions

- Ubuntu 18.04 LTS and newer versions need only one partition, the root partition, **/**, in a disk with the old style MSDOS partition table.

- But in a disk with the new GUID partition table, GPT, Ubuntu needs anther partition (with a 'bios_grub' flag to boot in BIOS mode or an EFI system partition, ESP, to boot in UEFI mode. It may help with the 'boot' and 'esp' flags). I suggest that you create an GPT partition table. See details at [this link: "Disk Space - Required partitions"](https://help.ubuntu.com/community/DiskSpace).

If you let Ubuntu use the whole drive and create the partitions is wants, you should get a working partition table with the necessary partitions.

- Additional to these partitions you can have other partitions, and I suggest a data partition with the NTFS file system in order to store data, that can be accessed both from Ubuntu and Windows. Maybe it is easiest to do this after installing Ubuntu, to use gparted, again when booted from a live drive (USB or DVD) to shrink Ubuntu's root partition and then use the unallocated drive space to create this new partition with the label [FONT=Courier New]**data**[/FONT] and the NTFS file system.

[HR][/HR]
If you intend to keep this external drive connected to the same computer, you can run the installer 'like usual', when installing into an internal drive.

But if you want to avoid touching the internal drive, and maybe also make the external drive portable to other computers, you had better unplug, disconnect or otherwise disable the internal drive, and then do the installation to this external drive.

See [this link: "Step-wise instructions for installed system in a USB drive"](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312).

After the installation you can connect/enable the internal drive again and select which drive to boot via a temporay boot menu. In many HP computers you get this boot menu via the hotkey **F9** directly at boot.

---

### Post by oldfred on 2020-09-14
You may want to remove the SFS/dynamic partitions, anyway.
Some Windows tools do not work on those partitions, so you have unique configuration.
It was used more with old BIOS/MBR configurations as a work around for the 4 primary partition limit, but was unique to Microsoft. Most with MBR used primary, extened and then logical partitions.

Be sure to have good backups.
But some tools may convert in place.

[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

Other options also Aomei or even testdisk if only 4 dynamic partitions:
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by mastablasta on 2020-09-15
Partition Wizzard Mini Tool works well. i used it. but backup first, just in case planets are not properly aligned when you are doing it. :) seriously, **backup data before any disk or file system manipulation**.

also, you could get a 5 EUR USB stick (preferably USB 3.0) and install to that. if you just want to test it out, it will be a descent option.

installing it in virtualbox is another one and removes the hassle of rebooting when changing OS. you need about 4 GB of ram for that. the more ram you have, the better the experience.

---

### Post by C.S.Cameron on 2020-09-15
You can make the install to USB drive pretty much fool proof using a Ubuntu image file.
Sudodus has made some good ones.
See [https://askubuntu.com/questions/1273977/newbie-needing-help-installing-full-os-on-usb/1273991#1273991](https://askubuntu.com/questions/1273977/newbie-needing-help-installing-full-os-on-usb/1273991#1273991)

---

### Post by CelticWarrior on 2020-09-15
And on top of all the previous information you also want to familiarize yourself with installation methods, UEFI vs BIOS/Legacy/CSM.
Ideally you want the former if you have a UEFI machine but it isn't mandatory. And then you also need to familiarize yourself with the different partitioning types (GPT vs MBR/"msdos") and the relationship between those and the installation methods/modes. Modern Linux distros are flexible enough tyo install and run in different scenarios but Windows isn't. Windows striclty requires MBR for BIOS/Legacy/CSM and GPT for UEFI mode.

If your Windows 7 is the factory default there are 99,9% chances it's in "BIOS" mode even if the machine is an early UEFI one. UEFI mode became the standard around 2012 with Windows 8.

You want to install the second OS in the same mode the original one was installed so the dual-boot with Grub works, regardless of where it is or will be installed. The choice for the bootloader is another issue though. With the old mode only one bootloader can exist in the MBR and only one MBR per drive. The best strategy for dual-booting "BIOS" mode installed OSes with one in an external (or secondary internal) drive is to install the Ubuntu's bootloader (Grub) only in the same drive where its system partition is thus leaving the original Windows bootloader intact in the drive where Windows is installed. The result is directly booting Windows without the external drive (or the boot order set to the Windows drive) and only booting to Grub with the external drive connected and the boot order set to it. Grub then should give the default option for Ubuntu but also an option to boot Windows).

PS - Please seriously consider ditching Windows 7 which is obsolete and unsupported. Without security updates it became more dangerous the more you use it. If you've been using it with an internet connection then very likely it's compromised already.
If you need Windows then you MUST upgrade to Windows 10 and keep it updated, period. If you don't just install Ubuntu instead, the smartest choice.

---

