---
title: "Using boot USB Ubuntu to repair Ubuntu Install"
date: 2021-07-21
forum: Packaging and Compiling Programs
---

### Post by dpan622 on 2021-07-21
This area is as close as I've found to my issue and question as: "using of applications from source"On the page to "create a bootable USB" at:[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overviewThe](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overviewThe) overview suggests we can use the USB to:"Use tools installed by default on the USB stick to repair or fix a broken configuration"Somehow I've gotten both my Linux boot disk (Western Digital Black 1Tb) and my USB to not boot the hardware.It's bad enough that it seems that Microsoft is pissed that I left, kept my money, and are subverting my system (lol...)I had to go back into Windows10 [insert full-body shudder...] to reformat my USB install drive; it wouldn't boot either.I've stored my data files on another drive, the only thing that has run on the Linux boot drive is the operating system and a few installed programs.BEFORE I reformat the boot drive and reinstall... HOW do I use the Ubuntu/Linux USB created with "Rufus 3.14" to REPAIR INSTALLATION ??

---

### Post by oldfred on 2021-07-22
With Rufus, you have to be sure to create live installer in correct boot mode.
It creates either UEFI only or BIOS only versions of live installer. It must match, your installed system.
Most other tools create standard live installer that can be booted in either mode, but then you have to choose correct boot mode in UEFI boot menu.

First you have to analyze what the issue is.
If boot issue, this may help.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It may need other types of repairs like e2fsck to repair corrupted file system or or even a major chroot into system to reinstall some broken software.

I have many flash drives. Microcenter store is only a few miles away and at checkout, they have their flash drives. And it seems everytime, larger is cheaper.
But then with larger flash drives I have full install of Ubuntu, and space for most of the critical data that I want to backup. And have some flash drives with multiple ISO like gparted, Supergrub, Boot-Repair (still suggest ppa to get newest version), knoppix and maybe others. My first flash drive is so tiny I just about retired it, but found I could fit rEFInd on it. And when my system totally locked up (too many bootable devices?), rEFInd was the only thing that worked.

---

### Post by dpan622 on 2021-07-23
Sorry, I don't understand half of what you said, Oldfred.I don't remember if I used UEFI or BIOS only... I followed the directions for using Rufus to set up a USB boot drive on the Ubuntu site per the link I posted.HERE:  [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overviewThe](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overviewThe) I remember the instructions said "choose BIOS only" and the information in that window changed when I selected the .iso file (?).  < shrug >I don't know what ppa version is, or where to find it.I don't know where to find Boot-repair ISO.the Boot Repair link you sent has warnings all over it for stuff I don't understand if I should use or avoid.

---

### Post by oldfred on 2021-07-23
Your instructions are the older ones that mention Windows XP which was BIOS only.
Shows Rufus for UEFI systems that use gpt partitioning:
[https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi](https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi)

If you look at second option in Boot-Repair link, that is the adding of the ppa into your Ubuntu live installer.
Just three commands to copy, one at a time into Ubuntu live installer's terminal.

If your computer is newer than about 2012, then it is UEFI.
Microsoft has required vendors to install in UEFI boot mode since release of Windows 8 in 2012. User still could install in BIOS mode and upgrades from Windows 7 often were still BIOS.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since Windows required gpt partitioning with UEFI, if your drive says it is gpt, then Windows will be UEFI.
From Ubuntu live installer.
sudo parted -l

---

