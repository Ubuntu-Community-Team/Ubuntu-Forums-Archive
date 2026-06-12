---
title: "Windows 8/virtual box/ubuntu"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by squakie on 2013-02-06
Not exactly an ubuntu questions, but I have a new laptop on the way and of course it has Windows 8.  During it's warranty period I don't want to mess things up they don't support, so I doubt I'll be able to install Ubuntu as dual boot for a while.  With that in mind, I was wondering if anyone knows if there is a version of VirtualBox that will run ok in Windows 8 and support Ubuntu?  I was hoping someone in the ABS would possibly know.  I've tried the proverbial net search, and I haven't found anything that looks very promising for VirtualBox in Windows 8.

Also, I've heard all about this uefi, efi stuff, and to be honest have been lazy in my later years and just not read up on any of it.  But I have seen mention of it here on the forums when it comes to dual-booting with Ubuntu.  How difficult is it to set up a uefi Windows 8 PC to have 1 or more Ubuntu partitions?  How difficult is it to install Ubuntu for dual-boot on a Windows 8 PC (yep - I mean dual-boot, not wubi)?  What are the tricks to getting it to boot correctly?  I've read several posts here about problems when trying to set up for dual-boot on a PC that currently has Windows 8.  Is there a guide out there yet for this type of install?

Thanks!

---

### Post by squakie on 2013-02-10
Several reads, no replies.

---

### Post by Paqman on 2013-02-10
> **squakie said:**
> I was wondering if anyone knows if there is a version of VirtualBox that will run ok in Windows 8 and support Ubuntu?

According to the Virtualbox manual [Windows 8 is supported]("https://www.virtualbox.org/manual/ch01.html#idp7761936").

I'm not really up on UEFI machines either, there is some [documentation for Ubuntu]("https://help.ubuntu.com/community/UEFI"), but I don't know how current it is. AFAIK UEFI machines can also boot in legacy BIOS mode anyway, so there is a loophole if UEFI is proving to be a problem.

---

### Post by oldfred on 2013-02-10
It depends on what vendor and model you have. Some work well, some have to have several work arounds and some just do not work dual boot UEFI Windows 8 secure boot with Ubuntu. Ubuntu is using the same key, so it should work for everyone. If a Samsumg be hesitant. 

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Best to turn off secure boot in UEFI/BIOS, but keep in UEFI mode. Varies how you turn on or off as each vendor does it differently.
Systems need quick boot or fast boot turned off. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Actually with UEFI and then gpt partition the partitions are easy. There is no more 4 primary partition limit, it now is 128 :) .  All partitions then in gpt partitioning are, in effect, primary.

But really good backups are required both the efi partition and the Windows partitions. Do not delete any Windows partitions as some have issues booting without them.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
    
Use Windows Disk Tools to shrink the Windows partition and make unallocated space for Ubuntu. Reboot a couple of times to let Windows run chkdsk and make any other repair due to partition size change.

How you boot live installer is how it will install and it should be in UEFI mode, but some will only install in BIOS mode.

If you have an UltraBoot with Intel SRT that adds complications,

I have links to threads (or you can search forum for your brand) on successful (sometime with effort) installs for Lenovo, Dell, HP, Sony, Asus etc. But it may vary by model.

There is a bug in grub2's os-prober. It still creates BIOS entries which do not work with UEFI.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    Boot-Repair can auto fix that issue and some others with UEFI.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

            Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

       Dell XPS13 Details on how to install - UEFI and Intel SRT  in Post #10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

And some vendors just do not have UEFI correct. It even corrupts system with Windows.
       [http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by squakie on 2013-02-10
Thank you SO much!!  The laptop arrives some time this week - a Dell with an i5 processor - don't know anything about the motherboard, etc..  Think it will be ok or will there be some horror story associated with it? ;)

---

