---
title: "Installation Problems"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by nick334 on 2008-07-23
Hi, I've downloaded the Ubuntu 8 Desktop edition and burned it onto a CD and tried to boot from it. I've gone into BIOS and checked it boots from CDs first. When I boot, it loads a screen where I pick from XP Professional and Ubuntu. It doesn't load up the Ubuntu CD like it has before when I installed Ubuntu 7 on my old computer. 

If I choose Ubuntu it comes up with Grub4Dos and says CodeEnd 0x4IA38. It comes up with what I assume is the Ubuntu version of Windows Command line. It mentions Grub and Bash but I don't know enough about Ubuntu to try and fix this.

Is it a problem with the CD, the .iso file, the computer, the CD drive, XP or something else?

Thanks.

---

### Post by phidia on 2008-07-23
> **nick334 said:**
> When I boot, it loads a screen where I pick from XP Professional and Ubuntu. It doesn't load up the Ubuntu CD like it has before when I installed Ubuntu 7 on my old computer. 
Is it a problem with the CD, the .iso file, the computer, the CD drive, XP or something else?

Thanks.

When you boot a correctly burned/downloaded iso you should get a ubuntu menu. There is no option, with the exception of booting from the hard drive, for booting xp. Have you got a windows bootloader set up on this computer? But back to the problem make sure you ran md5sum on the downloaded iso and that it checks/matches the md5sums provided. Recheck your bios the cdrom should be the first device in boot order.

---

### Post by Victormd on 2008-07-23
> **nick334 said:**
> When I boot, it loads a screen where I pick from XP Professional and Ubuntu.

This should only happen after Ubuntu has been installed, through the Grub menu. If you're booting from the CD, the boot menu should only contain Ubuntu related options and NO Windows.

Like phidia mentioned, check your CD/ISO and maybe burn at lower speeds.

---

### Post by dadspet on 2008-07-23
> If I choose Ubuntu it comes up with Grub4Dos and says CodeEnd 0x4IA38. It comes up with what I assume is the Ubuntu version of Windows Command line. It mentions Grub and Bash but I don't know enough about Ubuntu to try and fix this.
--------------------------------------------------------
with ubuntu 8.04.1 I get the same screen indicating 'Grub4Dos and says CodeEnd 0x4IA38.'

I have Ubuntu (AMD64 version) installed as an "application" in WXP SP2 on a external usb attached HDD. When I boot up I get a selection screen for WXP or Ubuntu. WHen I select Ubuntu I get the screen that looks like a command line screen looking for a DOS command (No desktop). 

I had trouble installing Ubuntu from a CD (image downloaded from Ubuntu site). As ubuntu was trying to install Ubuntu from CD i kept getting a error after several minutes (looked like ti read the CD almost to the end) indicating "Can't access CD another application might be using it - close out all applications using the CD" As far as I know no other applications were using the CD. Finally I loaded a virtual drive and mounted the Ubuntu image (I burned the CD with ) in the drive. It then seemed to install correctly but when I try to run it I get the GRUB4DOS   0.4.3 error or screen looking like a command line interface instead of a desktop. BTW I did check the CD with the check CD app in Ubuntu that comes up  when you load UBUNTU from a CD (Not installed in WIndows).

Any idead or help here.

---

### Post by appi2012 on 2008-07-23
The grub4dos thing is from a wubi install. You must have clicked install within windows, or accidently run wubi.exe. Try booting into windows, and going to add/remove programs. Try to find ubuntu, and uninstall it. Then i would recommend re-downloading and re-burning the ubuntu cd, following these instructions:
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

Then just close the ubuntu install application that comes up when you insert the disk into windows. After that, reboot, and boot off of the cd. Then, ubunty should ask for a language. select it, and then select:
"Try ubuntu without any change to my computer" That should load a almost fully working desktop. From there, double click on install, and follow the on screen instructions. 

NOTE: The instructions above are for installing ubuntu the real way, if you want to install it within windows, while in windows, insert a ubuntu cd that works, and select the "Install within windows" option.

Hope that helps!

---

### Post by mlentink on 2008-07-23
@ appi2012

You beat me to it.

@nick334 and dadspet
Guys, please make sure exactly how you installed ubuntu. Chances are you did not install ubuntu in a real dual boot config, but through wubi. Nothing basically wrong with that, but things work out a  bit different. 

please always make sure what you're booting from!

---

### Post by dadspet on 2008-07-23
> The grub4dos thing is from a wubi install. You must have clicked install within windows, or accidently run wubi.exe. Try booting into windows,

But thats exactly what I'm trying to do - install ubuntu into a window folder without changing my WXP installation. I don't want to reformat or repartition my HDD.

> Try to find ubuntu, and uninstall it.
It turns out that going to add / remove programs in WXP and trying to remove it does nothing. It won't uninstall. I had to do a system restore back to an earlier date to uninstall it.

When I try to reinstall it after the restore it doesn't ask me any more questions for the install so I think something from the previous install must be left around in the register. I keep getting the same error on reinstals. 

I don't think I'm ready for ubuntu - theres a lot of issues even on the install I can't imagine what issues remain if I ever got it installed. One I think is; I connect by USB wireless adapter and from what I read I don't think I will be able to connect to  the internet using a USB wireless adapter - major problem (but I guess If I can't install it that problem is irrelevant).

---

### Post by nick334 on 2008-07-24
I've uninstalled the Wubi thing and now it boots straight into windows, even when there's a CD in the drive. I've checked BIOS again and the order is Atapi CD-ROM, HDD. I've checked the .iso file with the MD5 checksums and tried burning another copy. That didn't work either. Shall I try burning at a slower speed? I've tried burning in both PowerISO which has worked many times before for other things and DeepBurner which has always worked.

When I'm in Windows and put the Ubuntu CD in and double click it, it comes up with the Ubuntu CD Menu with these options: demo and full installation, install inside Windows and learn more. Does this mean the CD works?

Could there be a problem with my computer because there isn't a problem with the .iso file, the burnt CD or the BIOS boot order.

---

### Post by nick334 on 2008-07-24
This is annoying.

I've checked and rechecked the boot options in BIOS and even only enabled booting from CD. I've tried 3 different Ubuntu discs - 2 of Hardy and 1 of Gutsy. I know the Gutsy CD does work as I used it on my old co puter and it worked perfectly. I even tried the XP disc I used to install XP on this computer about 2 weeks ago. I am certain that disc works - but my omputer couldn't boot from it.

It said something along the lines of "Insert bootable media and press any key". Nothing has worked.

All these CDs are detected in Windows though - I can open them and see the files. I can play DVDs and CDs perfectly.

Why can't I boot from CDs at all? It worked 2 weeks ago when I installed XP.

---

### Post by nick334 on 2008-07-25
Anyone?

---

### Post by Iceni on 2008-07-25
Do you have a windows cd or one of those annoying recovery cd's they give you with computers nowadays? Try booting with one of them, if they work there is wrong with the live cd's, if not there is something hardware related or bios settings related..

---

### Post by nick334 on 2008-07-25
Nope tried it before and again just now and it doesn't work with my XP CD which I used when I got this computer 2 weeks ago.

---

### Post by nick334 on 2008-07-25
How else can I install Ubuntu if I can't get this to work?

---

### Post by appi2012 on 2008-07-25
You could install through wubi. Download it from here:
[http://wubi-installer.org/](http://wubi-installer.org/)
That should install ubuntu inside windows, and not do any partitioning. However, wubi is much more sensitive to hard reboots (holding down the power button to turn it off) If you turn it off like that, sometimes it will give you a HAL error. To fix that, look at this page:
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

If you really want to install ubuntu the real way, try upgrading your bios, and then trying to boot from cd.

---

### Post by appi2012 on 2008-07-25
dadspet:
try using this to uninstall:
[https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe)

download wubi from here:
[http://wubi-installer.org/](http://wubi-installer.org/)

when you run it, make sure it is in a different folder than your ubuntu ISO

nick334:
about hard rebooting alteratives:
There are normally several ways to reboot cleanly using key combinations such as:

    *

      CTRL + ALT+ F2 (get to a terminal, you can then run top/kill/pkill to discover and kill the offending process)
    *

      ALT+ SYSRQ + R then CTRL + ALT+ F2 (as above, but first try to regain control of the keyboard)
    *

      CTRL + ALT + Backspace (kills the graphic session and goes to a console, all graphical applications are terminated too)
    *

      ALT+ SYSRQ + R then ALT + Backspace (as above, but first try to regain control of the keyboard)
    *

      CTRL + ALT + DEL (reboot)
    *

      ALT+ SYSRQ + R then CTRL + ALT + DEL (as above, but first try to regain control of the keyboard)
    *

      ALT+ SYSRQ + R + S + U + B (forces a clean reboot even when the keyboard is not responding)

The last one is the most effective, but you could try the other commands first.

---

### Post by nick334 on 2008-07-25
I just want to install from the CD. I don't see why I can't - the CD is fine, the .iso is fine, the BIOS settings are fine and the CD drive is fine. I don't see why booting from my XP CD worked 2 weeks ago but now I can't boot from any CD.

---

### Post by nick334 on 2008-07-26
Any help?

---

### Post by e_james on 2008-07-27
At this moment I can't remember enough details but I think I read somewhere that the modern bios has a memory. It has something to do with detecting hardware changes. In some circumstances, yours may be one of them, it is necessary to flush out this memory so that the hardware is detected correctly. I think one way to do it is to remove the cmos battery for at least an hour. This may not be an option if we are talking about a laptop.

---

### Post by halitech on 2008-07-27
> **nick334 said:**
> Nope tried it before and again just now and it doesn't work with my XP CD which I used when I got this computer 2 weeks ago.

> **nick334 said:**
> I just want to install from the CD. I don't see why I can't - the CD is fine, the .iso is fine, the BIOS settings are fine and the CD drive is fine. I don't see why booting from my XP CD worked 2 weeks ago but now I can't boot from any CD.

I hate to disagree with you but if you can't boot from any cd now, you have a problem and its either your BIOS is not set to boot from the cd (which I don't think is the case) or your cd rom is toast (most likely case)

---

