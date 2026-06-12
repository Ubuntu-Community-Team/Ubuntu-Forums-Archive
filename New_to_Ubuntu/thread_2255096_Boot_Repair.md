---
title: "Boot Repair"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by Munnubalu on 2014-12-02
[FONT=arial]Hi,[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I had Windows 8 on my HP laptop and installed Ubuntu 14.04 on another drive. However, after installing, I am not able to get access to my Windows drive. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I tried boot repair and got the below url :[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/9322736/](http://paste.ubuntu.com/9322736/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Could you please help get back the windows drive[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Regards[/FONT]
[FONT=arial]Jishnu [/FONT]

---

### Post by westie457 on 2014-12-02
Hi Munnubalu and welcome to the Forum.
After looking at your Boot Repair report unfortunately it is bad news all the way.
You have only the one hard drive in your machine and there is no sign of Windows on that hard drive.
If Windows was on that hard drive there is little to no chance of getting Windows back.

When you installed Ubuntu which option did you use in the Installer menu?

---

### Post by grahammechanical on 2014-12-02
> [COLOR=#000000][FONT=arial]I had Windows 8 on my HP laptop and installed Ubuntu 14.04 on _another_ drive.[/FONT][/COLOR]

Is Ubuntu now booting correctly? Where is the drive with Windows 8 on? Is it still in the machine? Here is some advice to follow when we install Ubuntu on a machine with Windows 8 pre-installed.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It is my understanding that on a machine with Windows 8 pre-installed Windows 8 will always be installed using EFI mode.

This was the problem found by Boot Repair

> [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.

If the Windows 8 disk was in the machine when Ubuntu was installed it is mostly likely that the Ubuntu boot loader was installed in the MBR of that disk. By removing the Windows 8 disk you removed the Ubuntu boot loader and Boot Repair found a problem and solved it but the Ubuntu boot loader now has no knowledge of Windows 8 and the boot partition in sda1 does not have any boot files for Windows 8.

I suggest that you reconnect the Windows 8 disk and then run Boot Repair again.

Regards.

---

