---
title: "[HELP] Install Ubuntu 15.10 dualboot Win8.1 UEFI"
date: 2015-11-27
forum: New to Ubuntu
---

### Post by Mato_xXx on 2015-11-27
Hello I have notebook Lenovo G50-70 with legal Windows 8.1 PRO on UEFI with Secure Boot ON for fast booting. But now for my developing I need Ubuntu so I want install it. I chose Ubuntu GNOME 15.10 because it is newest so I think it will be most compatible with my notebook. But I need your help with installing process, I searched on internet but can not find any good solution for me. I want install it as secondary OS with Windows bootloader as primary for fast boot and GRUB after rebooting system. But I want it on same drive and I don't know how to install it correctly without any losing my data or overwriting bootloader or losing fast booting on Win.
Thanks for your answers and if I post it in bad section then sorry, this is my first thread on this forum. :)

---

### Post by grahammechanical on 2015-11-27
There are some things that are technically possible but practically very difficult to do. And then there are those things that don't come close to be technically possible.

> install it as secondary OS with Windows bootloader as primary for fast boot and GRUB after rebooting system.

The Windows boot loader will not recognise any other operating system other than a Microsoft operating system. And Windows fast boot will have to be turned off because fast boot is actually restarting from hibernation and that will cause problems with installing Ubuntu in a dual boot with Ubuntu.

These are the guidelines that you should follow.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

> 
To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 


[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 


[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.    


[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 


[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 

[/LIST]


If the machine came with windows 8.1 pre-installed then Windows 8.1 was installed in EFI mode. And there is something else you should be aware of. There are many posts on this forum where people have been successfully dual booting with Windows 8.1 and then they upgraded to Windows 10 and the upgrade broke Ubuntu. Check out those posts and see what to expect. You might decide to upgrade to Windows 10 before installing Ubuntu.

Regards

---

### Post by Mato_xXx on 2015-11-27
> **grahammechanical said:**
> The Windows boot loader will not recognise any other operating system other than a Microsoft operating system.

But easybcd can add Ubuntu and then it will recognize it.

---

### Post by yancek on 2015-11-27
> But easybcd can add Ubuntu and then it will recognize it. 				

Not according to the neosmart site at the link below which explains why it doesn't work with UEFI.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

### Post by Mato_xXx on 2015-11-27
OK so I need use Legacy mode as I understand??? Or I need reinstall Windows??? And what if I install Ubuntu on secondary HDD??? Because I really love my fast booting of Windows and I will not use Ubuntu that much so I don't want GRUB as my bootloader.

---

### Post by Mato_xXx on 2015-11-29
So I tryed to install Ubuntu on my Lenovo with Secure Boot OFF, Fast Boot OFF and Ubuntu boot partition on his own / partition. But now I got two separated boot loaders. One Microsoft Windows boot loade and second Ubuntu loader and I tryed almost everihning but I can not find how to add Ubuntu boot order to Windows boot loader at all... :( I don't like GRUB and now my notebook is booting longer for 5sec that is long time. If I want to boot to Ubuntu I need shut down and power it with special lenovo button and go to boot menu and chose Ubuntu bootloade. Is any way to make it normal???

---

