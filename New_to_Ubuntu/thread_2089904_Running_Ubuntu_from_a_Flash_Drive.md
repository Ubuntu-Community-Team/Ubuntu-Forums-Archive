---
title: "Running Ubuntu from a Flash Drive"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by PingPirate on 2012-11-30
Alright... I posted this in beginners, but I'm open to it being moved if it's not really a beginner's question. The fact is that I have some experience with Ubuntu but not much.

I know that, using a tool like Unetbootin, I can install all sorts of Linux distros, like ubuntu, on my flash drive. But that installation for ubuntu is just the disc image - where you can "try ubuntu", or install it on the current system.

I'm not sure if it's possible - or even a good idea - but, can I make a full installation to the flash drive? When  attempting to run the ubuntu installer within windows, it automatically downloads a version tailored to my hardware - amd64. Ideally, I'd like this to run on any processor/machine I attach the flash drive to and boot.

The end goal is to diagnose any system hardware problems, make operations on the internal hard disks without booting from them (eg for windows repair), or just kind of have a mobile workstation that would work anywhere.

Another possibility: could I modify that iso for Unetbootin to set up the tools that I want installed when I run from the flash drive?

---

### Post by sandyd on 2012-11-30
> **PingPirate said:**
> Alright... I posted this in beginners, but I'm open to it being moved if it's not really a beginner's question. The fact is that I have some experience with Ubuntu but not much.

I know that, using a tool like Unetbootin, I can install all sorts of Linux distros, like ubuntu, on my flash drive. But that installation for ubuntu is just the disc image - where you can "try ubuntu", or install it on the current system.

I'm not sure if it's possible - or even a good idea - but, can I make a full installation to the flash drive? When  attempting to run the ubuntu installer within windows, it automatically downloads a version tailored to my hardware - amd64. Ideally, I'd like this to run on any processor/machine I attach the flash drive to and boot.

The end goal is to diagnose any system hardware problems, make operations on the internal hard disks without booting from them (eg for windows repair), or just kind of have a mobile workstation that would work anywhere.

Another possibility: could I modify that iso for Unetbootin to set up the tools that I want installed when I run from the flash drive?
Its possible - you can just install to a flash drive.

One thing - make sure the bootloader is _installed_ on the flash drive, not the HDD of the computer. This is specified during setup.

Also, be aware that flash drives have a limited number read/writes

---

### Post by ajgreeny on 2012-11-30
> **PingPirate said:**
> The end goal is to diagnose any system hardware problems, make operations on the internal hard disks without booting from them (eg for windows repair), or just kind of have a mobile workstation that would work anywhere.

Another possibility: could I modify that iso for Unetbootin to set up the tools that I want installed when I run from the flash drive?
If this is really the reason for you wanting to run Ubuntu, whilst not actually a bad idea, you might like to consider downloading and then running a live CD of one of the many  distros available that can be used to rescue a system, eg [http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

See more possibilities at [http://www.softpanorama.org/Freenix/minidistributions.shtml](http://www.softpanorama.org/Freenix/minidistributions.shtml)

---

### Post by cksum7 on 2012-11-30
> **ajgreeny said:**
> If this is really the reason for you wanting to run Ubuntu, whilst not actually a bad idea, you might like to consider downloading and then running a live CD of one of the many  distros available that can be used to rescue a system, eg [http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

See more possibilities at [http://www.softpanorama.org/Freenix/minidistributions.shtml](http://www.softpanorama.org/Freenix/minidistributions.shtml)

I agree...live CD is the way I use Linux on computers that I cannot load the OS on the HD.

---

### Post by monkeybrain2012 on 2012-11-30
Yes, it is possible to install in a flash drive if it is big enough (8 G would be ample). 

I assume by installing in a flash drive you mean a real installation and not a live usb (for testing and installation only). A full installation has the advantage that you can install proprietary graphic cards, update system components and kernels. It is a full Ubuntu install. The catch is that it may be a bit slow (don't know if it would make a difference with usb3) It is true that flash drive has limited r/w but it shouldn't be an issue for normal usage, I had made one for 10.04 that lasted for 6 months (and then I erased it for something else, it just died not long ago after many, many rewrite which I don't think is typical for normal usage)

A live usb with persistence allows you to save settings, data and install some software but it doesn't allow updates for many system level stuffs, kernel or proprietary graphic cards etc so if you run update in your live usb without looking at what is being updated it is very likely to break your system. Also since it is in FAT format it has a limit of 4 G. The advantage is that it runs fast because it runs out of ram.

I won't recommend "burning a live CD" unless your machine doesn't support usb boot and all you want to do is to install Ubuntu. First of all it is painfully slow and secondly you cannot install anything as you lose all your data and settings on every reboot. So unless everything just works without needing any update or reboot, it doesn't help a lot if things require a bit of non trivial tweaking to work.

---

### Post by oldfred on 2012-11-30
I have a full install in an 8GB partition of my 16GB drive and then I boot as ISO using grub loopmount several other repair ISOs in my other 8GB partition.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
    
Windows only sees the first partition, so if you want some compatibility with Windows you also need a NTFS or FAT32 as the first partition. 

If booting different systems you may have 32bit vs. 64 bit (only 32bit boots both) and video issues to manually work around. 

Install to flash drive is like any install to a second drive internal or external and you have to use manual install to get the choice on where to install the grub2 boot loader.
       Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

    
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

    
       This will boot an ISO from a hard drive. (Same for flash drive, just path may vary.)
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by PingPirate on 2012-11-30
Wow thoroughly impressed by the responses. Thank you for bringing to my attention that flash drives only have a limited amount of read/writes. I totally forgot about that... and the flash drive I'm using happens to be pretty cheap too - might risk wearing it out quickly.

I think for the original goal I had for this idea, I'm going to go with SystemRescueCD. I've used programs like BartPE before, and SystemRescueCd is pretty much what I need. But I'm excited to look in to several of these ideas.

You guys have given me plenty of reading material.

---

### Post by GregA on 2012-11-30
Another great Live CD distro is "Partition Magic" - - it runs on most systems utilizing ram, , so you can actually use it instead of waiting for disk load times.

---

