---
title: "Crashed again,  can't install anything now."
date: 2013-04-15
forum: New to Ubuntu
---

### Post by Eersfanpilot on 2013-04-15
In summary, been having issues with Ubuntu 12.10 crashing repeatedly. ( Dual boot Windows 8 )

Crashed after sleep mode, crashed after my laptop battery died.  Took several attempts to get it reinstalled. Yesterday it was back up and running,  then crashed applying updates and never came back. I have tried repeatedly to get a fresh install ( about the fifth install) and now I can't get any version to install. I have tried 12.10, 12.04  and even 13,  all for 64 bit. I've tried purging Grub. 

Installation error is failing to find kernel ("must load kernel first").
 MD5's match

 What else can I do? 

 Has the  suspend/ wake issue been fixed in the upcoming 13 release? 

 Right now only Windows is on the machine. I can not even get a Live USB to install or go into trial before install.


 Computer 
 Lenovo Z585 A10

---

### Post by Eersfanpilot on 2013-04-15
Bump,  any ideas?

---

### Post by Cheesehead on 2013-04-15
Multiple crashes are rare, and sometimes indicate failing hardware.
Do you remember any of the crash error messages? Were there any?

The error message you give seems to indicate a misconfigured LiveUSB.
How, exactly, are you creating it? Is it the same LiveUSB that worked successfully before?

Are you saying the USB stick is not recognized at all (BIOS issue) or that the LiveUSB tries to load and fails?
The latter is usually fixed by re-creating the LiveUSB stick.

---

### Post by Eersfanpilot on 2013-04-15
I was never able to see any error messages.  After each crash it would not boot. I could, a few times,  get to recovery to check for broken packages but it never found any. 

 After every crash it would boot to a screen with a bunch of [OK]  on the right side but then it would freeze,  this was after every crash. 

I created the LiveUSB via Unetbootin. It is the same 15G USB I have used to get successful installs. 

 How much space should be used on the USB once the iso is created?  Mine shows formatted and blank with 15.1  available but once the iso is created it has 15.  Seems small to me.

---

### Post by Eersfanpilot on 2013-04-15
Now,  any time I try to install any flavor it can not find the kernel.

---

### Post by UltimateCat on 2013-04-16
Depending on how old your Lenovo is it could be overheating but generally Toshibias are more notorious for overheating.

Does your Lenovo have a dvd/cd drive?

If so; go and get the LIVE ISO IMAGE of Ubuntu and burn it to DVD/CD and you could install your distro that way--
Manually create a partition: ext3 (/) journaling file system for Ubuntu about 20GB
Than create a partition dev/sda for the swap (if Win's 8 will let you)

With Windows 8 you have to disable the secure boot--

[http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html](http://www.eightforums.com/tutorials/17058-secure-boot-enable-disable-uefi.html)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/](http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/)
[http://www.linuxquestions.org/questions/slackware-14/slackware-on-uefi-4175448945/](http://www.linuxquestions.org/questions/slackware-14/slackware-on-uefi-4175448945/)

You can try a LIVE cd and run:
```
fdisk -l

```
That's a small letter L.
That will show you all of the partitions on your computer.

It may be that you don't have a large enough USB Memory Stick-- Or like Cheesehead mentioned it's not formatted correctly-

When I installed Ubuntu I allocated 20GB for the journaling file system (/) ext3
And than I allocated an additional 2GB for the swap partition-

Hope that helps

---

### Post by UltimateCat on 2013-04-16
> **Eersfanpilot said:**
> Now,  any time I try to install any flavor it can not find the kernel.

The **Could not find kernel image: linux** error typically occurs on USB flash drive [[COLOR=#009600][COLOR=#009600 !important][FONT=inherit !important][COLOR=#009600 !important][FONT=inherit !important]Linux [/FONT][/COLOR][COLOR=#009600 !important][FONT=inherit !important]installations[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/#") if syslinux could not find the configuration file *syslinux.cfg*.
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/)

---

### Post by Eersfanpilot on 2013-04-16
Update and thanks to those that helped. I was able to get back to using " Live"  session by burning 13.04  to a DVD.  However once I tried to install it kept giving me an " installer had crashed"  error.  Which sucks cause I really liked what I had seen from Ubuntu but all these stability bugs are just unacceptable. 

 My other spare blank DVD was loaded with Fedora 18.  It is functioning much faster and does not crash,  maybe one day I'll be back to Ubuntu but for now,  off to Fedora.

---

