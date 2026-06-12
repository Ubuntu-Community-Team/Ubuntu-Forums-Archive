---
title: "Install On A New PC with A Clean HD"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by davedo2 on 2013-02-01
I will be receiving a new 64-bit PC that shipped with Windows 8, but I told my brother he could have the HD. Since this is a UEFI PC what will I need to do to install Xubuntu 12.04 or 12.10 on it?
That is, Xubuntu only, no windows. Will UEFI hamper the install or is there anything special I will need to do to enable the install?

Alternatively, and even better for me, could I put a HD with a working Xubuntu system in this new PC instead of doing all the work of a new install? Same question really: are there problems with UEFI to overcome or anything special I would need to do or know?
This is new territory for me, I know zero about windows, so any help offered will be very much appreciated. Thanks...Dave

---

### Post by BlinkinCat on 2013-02-01
Hi,

I have no idea myself, but this may help -

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Cheers - :P

---

### Post by ACubed10 on 2013-02-02
good luck with the install, and great choice!  I'm a Microsoft Tech, and I  can't stand Windows 8.  I only use Ubuntu and Mac OS X. I love those paychecks though! :popcorn:):P

---

### Post by audiomick on 2013-02-02
> **davedo2 said:**
> 
Alternatively, and even better for me, could I put a HD with a working Xubuntu system in this new PC instead of doing all the work of a new install? Same question really: are there problems with UEFI to overcome or anything special I would need to do or know?

I haven't tried that, but from what I have read, success has a fair bit to do with whether the installed system has proprietary drivers on it or not. For instance, if you have an nVidia graphics card on the system the drive came from, and something else on the system it goes in to, you are likely to have problems. If the only drivers in use are the default ones, I gather it can be a plug in and go process. 

You will, of course, have to point the BIOS (EFI) at the drive to boot from it.

I am guessing now, but I expect that if the pre-installed drive is set up under BIOS / MBR, you could well have problems with it in a machine that is using UEFI. 

Hope that helps a bit...

---

### Post by Paqman on 2013-02-02
*disregard, having a brainfart*

---

### Post by grahammechanical on 2013-02-02
That machine will have Secure Boot. At the moment only Ubuntu 12.10 and flavours of 12.10 will install with secure boot enabled. Some also recommend turning off Fast Boot.

If you put a hard disk with an operating system already on it and it is not 12.10 and secure boot is enabled then the UEFI will not accept the OS as a certified OS. The Grub on the hard disk might be set up for a BIOS boot and not an UEFI boot.

Regards.

---

### Post by davedo2 on 2013-02-02
Michael, thanks for your help, but I'm a bit confused about a few things:
1. how do I tell what, if any, proprietary drivers are on the drive? Can I safely remove them?
2. What do I need to do to "point the BIOS (EFI) at the drive to boot from it."
3. The existing drive is on an older 64-bit PC and is running Xubuntu 12.04, it's not on a UEFI PC, so I guess your last comment sounds ominous.
I could upgrade the existing system to Ubuntu 12.10 Secure-Remix, would that solve the UEFI problem?

---

### Post by oldfred on 2013-02-02
UEFI systems also have a BIOS/Legacy/CSM mode that works just like the old BIOS. And you then should be able to use old drive, just any proprietary drivers (usually video) may need to be turned off. You may just need nomodeset to boot.

And if doing a new install, how you boot installer from UEFI menu, either UEFI or BIOS mode, is how it will install.

You will have to in UEFI/BIOS turn off fast boot as with some systems you cannot get back into UEFI except from Windows 8 with fast boot on.
You need to turn secure boot off. Some systems have a setting for secure boot on/off, others seem to have a UEFI on which means secure boot off. 
If you want legacy boot then you should also have a setting for that, but may not work unless secure boot is off. There is no secure boot with BIOS mode.

Windows 8  systems also use gpt partitioning. Ubuntu will work with gpt partitioning with UEFI or BIOS but needs different extra partitions. With UEFI both Windows and Ubuntu use the same efi partition. With Ubuntu and BIOS mode on gpt you need a small 1MB unformatted bios_grub partition. 

Note Windows will not boot from gpt with BIOS mode. 
Your brother will have to either boot in UEFI mode, or erase Windows and add bios_grub or totally convert to MBR and run fixparts to remove all gpt meta-data from drive.

---

### Post by davedo2 on 2013-02-17
Well, it wasn't exactly what I hoped for. I booted with a Ubuntu 12.10 secure-remix DVD to see if it would take & for the heck of it did a dual-boot install. Naturally windoze hated that & wouldn't admit ubuntu was resident, but boot repair on the dvd fixed that problem. However, it was so much effort to get things going I think I'll wait a bit for a clean install on a new HD. In the interim a new problem: the PC doesn't recognize my Ethernet connection (I've tried two good lines that work on other PCs in the room) so I'm reduced to connecting via wifi - a *major* slowdown. It's an HP Pavilion HPE h8-1360t. Any ideas on what I need to do to get the wired connection working? I've never, ever had a problem with that before. Thanks for any advice...Dave

---

