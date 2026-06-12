---
title: "Booting, Inspiron 17R (5720, Mid 2012) Windows 8, now Ubuntu 14.10."
date: 2014-12-20
forum: New to Ubuntu
---

### Post by Aberts10 on 2014-12-20
SOS! Currently one of my friends is having a issue with there ubuntu 14.10 installation, and his bios will not work at All, it just goes into the Grub after passing the DELL loading screen that says press F12 to open boot options.
**Inspiron 17R (5720, Mid 2012) Preloaded with windows 8 (not 8.1)**


Now its having some problems on ubuntu and we need to use a ubuntu usb installation flash drive to re-install ubuntu, but when it boots it says in quote "(Press F12 for boot options)" in the bottom right corner, we pressed F12, Fn + F12, F1, F2, F3, F4, F5, Etc..... nothing goes into the bios and everytime it just goes into grub.

How am i supposed to restore it if theres no windows 8 anymore, no option in grub for usb boot, and NO working bios?!

Also one more thing, when ubuntu was installed it overwrote the windows partion because it did not see it installed.

---

### Post by ajgreeny on 2014-12-20
What are the problems you are having in the installed Ubuntu?

We may be able to solve that problem for you and at least get back to having an OS you can use, but we need to know what is wrong at the moment.

Do you know if the operating systems, or Ubuntu if it is the only OS you have now, are installed using UEFI or legacy BIOS; I suspect not UEFI as it is a 2012 machine, but it may still be UEFI; we need to know.

However, I am mystified as to why you can not get it to boot to a USB, assuming you used that to install in the first place.  Can you try a DVD or is there no optical drive?

---

### Post by Aberts10 on 2014-12-21
I belive it _WAS_ UEFI but not ubuntu wont detect the windows 8 partion because it erased it. now when it boots it goes directly into grub after showing the Dell logo and in the bottom right corner "press f12 to open boot options" which obsiouly doesn't work. it lists UEFI, but then when it tries to start that partion it gives a error saying that it could no locate the partion image.

Another problem with the computer is that its "slowing down", and ubuntu is showing a system error that it cannot report to the developers. Not only that but the person that owns the computer likes to record videos for youtube, and he cannot hear people in skype calls anymore. Windows 8 is NOT listed anymore in grub, so he cannot use it to boot. But when we tried F2, it brought us into a specialized configuration tool of some sort, that was probably used to setup the computer. At this point the owner just wants to re-install the operating system Etheir windows or linux, or get the problems fixed, and as a side note he does _**NOT**_ have a cd that is big enough to install anything bigger than 750 MB.

**NOTE: This is NOT my laptop and do not have physical contact with it, but i am able to use teamviewer, and video chat to help the person out, currently i told him he will probably need some sort of medium at least 4 GB to 8 GB and he ended up getting a 4 GB USB flash drive.** **Also in my past history when i installed ubuntu onto a Dell Inspiron i had some of the same issues, but i also had a GUI issue and sometimes even the GUI wouldn't show at all, and all the same problems with the error messages that couldn't report themselves, but it would just get worse and worse over time and i am afraid this is what will happen.**

---

### Post by Aberts10 on 2014-12-21
[B]Just discovered something new with windows 8 computers.

Because windows 8 boots too fast they changed the way the computer starts with the New UEFI Advanced Boot menu.

i think that we cant access the boot menu because of the fact that windows 8 partion is gone. meaning that there IS no UEFI or Advanced Boot menu.

This would explain why we cannot access any type of boot menu, but does this also mean that because windows 8 is gone we are screwed?
[/B]

---

### Post by oldfred on 2014-12-21
Some systems may require you to totally cold boot to get back into UEFI. If laptop then also remove battery and hold power switch for 10 sec to drain power. Then see if you can get into UEFI/BIOS with correct key for your system.

This is for a different model, but the discussion seems to apply to all Dell's with Intel chips.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Dell provided sputnik to fix issues with Ubuntu 12.04, but all those fixes are in 14.04.

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

All models of Dell seem to be similar, but differenent screen sizes and options, but UEFI settings should be the same for common features.

 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

