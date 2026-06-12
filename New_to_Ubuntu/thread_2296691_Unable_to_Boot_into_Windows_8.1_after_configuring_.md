---
title: "Unable to Boot into Windows 8.1 after configuring dual boot"
date: 2015-09-28
forum: New to Ubuntu
---

### Post by Puneet_Gupta on 2015-09-28
I am new to ubuntu. After setting up ubuntu for dual boot through instructions found on google, now I am unable to boot into windows 8.1. Windows option is not showing up in the boot menu. Here are the results after running bootinfoscript.
[ATTACH]264702[/ATTACH]

---

### Post by grahammechanical on 2015-09-28
Did your web search find this document?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please confirm that you followed the general principles outlined in that wiki page.

> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in UEFI mode:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"). This is a problem if 32-bit UEFI is the only way your computer can boot, e.g. if you have a modern Intel Atom based laptop. In this case, you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").)[/FONT]
[*=left][FONT=inherit]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[*=left][FONT=inherit]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. [/FONT]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[/FONT]
[/LIST]


A computer with Windows 8.1 pre-installed would most certainly be install in EFI mode. 

Regards.

---

### Post by Puneet_Gupta on 2015-09-28
No I didnt follow these steps.
Rather I followed these steps to install ubuntu.
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
and later ran boot repair as stated here
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
But I was unable to disable secure boot as the option was not showing up.
I still have my windows files intact in 1 HDD and ubuntu in other I guess.

---

### Post by yancek on 2015-09-28
Your boot repair output actually shows windows installed in MBR rather than UEFI.  There is no EFI partition on sda (windows disk) but there is an EFI partition on sdb (the Ubuntu disk) which has the correct Ubuntu EFI files.  You should not mix MBR and UEFI.  You have also installed Grub boot code to the master boot record of both drives thus overwriting the windows boot code in the MBR of the windows disk.  Installing Ubuntu in MBR and putting it's boot code in the master boot record of the smaller drive would have eliminated this problems.  I don't use EFI so perhaps someone more familiar with it will have a suggestion to repair.

---

### Post by oldfred on 2015-09-28
Did you install Windows 8 yourself?
Windows 8 from vendors is always UEFI, but yours is BIOS with MBR partitioning.
And you installed Ubuntu in UEFI mode on a MBR partitioned drive? UEFI standard is gpt partitioning.
And then you installed grub to both MBR's & to the partition boot sector of the Ubuntu install on sdb5.
Since Windows is BIOS boot, best to keep Ubuntu as BIOS boot. UEFI & BIOS are not compatible and you can only dual boot from grub is both are in same boot mode.

If you boot Ubuntu in BIOS mode and run this does it add Windows to grub menu?
sudo update-grub

Best just to have grub in the MBR of sdb and to keep the Windows boot loader on the MBR of sda. While grub will let you boot Windows, you could then use the Windows boot loader on sda if errors with grub or drive sdb.
You can use Boot-Repairs' advanced mode to choose Windows & sda to install a Windows boot loader to sda. Or use your Windows repair CD or flash drive to do the same.

---

