---
title: "HP Desktop with Win 10 Pre-installed - UEFI Dual Boot Method"
date: 2016-05-14
forum: New to Ubuntu
---

### Post by kraus37043 on 2016-05-14
The methods to enable UEFI and disable it on new HP desktops are frightening. I have reviewed many tutorials for other PC makers and none has the red windows or require you to type a 4 digit number to proceed. The message I perceive is "If you don't know exactly what you are doing stay out of here!" I finally found a link that describes my system:

[http://www.support.hp.com/in-en/document/c04784866#AbT2](http://www.support.hp.com/in-en/document/c04784866#AbT2) (Using Secure Boot on a Desktop Computer is about 2/3 down from the top)

I would like to be able to dual boot ubuntu 16.04 and Win 10 in UEFI mode. I am currently using Ubuntu 16.04 with grub 2 on an old Vista Computer. I used Pendrive Linux to install the iso. I don't think that iso is UEFI compliant.

Can anyone point me to a tutorial, or better yet, a youtube video showing how to dual boot my HP PC with Ubuntu 16.04 and Win 10. I have some experience with Ubuntu, but UEFI has me thoroughly confused. I have seen many tutorials showing dual boot in legacy mode but have not found one for UEFI mode.

---

### Post by grahammechanical on 2016-05-14
All versions of Ubuntu are both UEFI & secure boot compliant have been since the October 2012 release of Ubuntu. The same image that installs on a machine with a BIOS boot system will also install on a machine with a UEFI boot system.

Have you see this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The actual installation process is the same. The difference with a UEFI boot system is that we need to run the Ubuntu live session in EFI mode then Ubuntu will be installed in EFI mode. And we need to do that because Windows 10 is installed in EFI mode.
> 
[h=2]Case when Ubuntu must be installed in UEFI mode[/h] Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]
 
[h=2]General principles[/h] To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 


[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 


[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.    


[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 


[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 

[/LIST]


That information is applicable for Windows 8 and 10.

Regards

---

### Post by kraus37043 on 2016-05-15
Thank you for the feedback.  Can I rely on the fact that all information in these forums applicable for windows 8 is valid for windows 10 as well?  My old PC was Vista and the new one Win 10.  

You state "The difference with a UEFI boot system is that we need to run the Ubuntu live session in EFI mode then Ubuntu will be installed in EFI mode."  I don't understand what I need to do to install Ubuntu to run the live session in "UEFI mode".

I know I have 64 bit Ubuntu 16.04 loaded on my USB drive.  I know my Win 10 is running in UEFI mode.  I lost the use of Win 10 twice before and had to reinstall it twice.  I did get the Grub 2 boot loader screen.  *Does that mean I had Ubuntu in legacy mode*?  If so, I don't know what I need to do differently.

The UEFI screens vary greatly by PC manufacturer.  Those of you who clicked on the link from my previous post will see that they are greatly different.  I am hoping that someone with a new HP desktop PC can supply me some screen shots of installation in secure boot mode.  

Let me ask a question again.  Is Grub 2 compatible with UEFI?

---

### Post by yancek on 2016-05-15
> Can I rely on the fact that all information in these forums applicable for windows 8 is valid for windows 10 as well

 Many of the members here use windows and are quite familiar with it but if you want reliable information on 'windows', I would suggest you go to a windows forum or the microsoft site. 

Selecting to install Ubuntu EFI is explained in the Ubuntu documentation at the site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The BIOS screens for different manufacturers to access/set UEFI setting vary greatly and I would suggest that you use the manual you got when you purchased the machine.  If you don't have that, do an online search for the 'manual' for your specific HP model computer.

---

### Post by kraus37043 on 2016-05-16
This is not a Windows issue, it is a UEFI issue.  HP has not been of much help.  They did offer to pay to have Ubuntu installed locally.  The first time I need to replace my hard drive or reload an OS, I am out of luck.  I need to learn how to do it myself.  I have two UEFI compliant OS's, one of which is preinstalled.  I believe GRUB 2 is compatible with legacy boot mode, but not UEFI.  Is that correct?  If it is, that explains why I have been unsuccessful so far.  Where can I acquire a UEFI only Ubuntu iso?

---

### Post by yancek on 2016-05-16
> I believe GRUB 2 is compatible with legacy boot mode, but not UEFI.

You should be able to install Ubuntu UEFI.  Did you read the detailed page at the link I posted above which is the official Ubuntu documentation on this subject?  
I think part of your problem is HP as they do not comply with the UEFI standards.

---

