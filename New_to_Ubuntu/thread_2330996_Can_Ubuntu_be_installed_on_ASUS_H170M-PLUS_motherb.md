---
title: "Can Ubuntu be installed on ASUS H170M-PLUS motherboard"
date: 2016-07-17
forum: New to Ubuntu
---

### Post by chenjennhaur on 2016-07-17
I am planning to buy a new PC with Asus H170M PLUS motherboard. I have checked the ASUS website and they only specify that they support windows OS
[https://www.asus.com/sg/Motherboards/H170M-PLUS/specifications/](https://www.asus.com/sg/Motherboards/H170M-PLUS/specifications/)

Does this mean that ubuntu would not work on this PC ?

---

### Post by grahammechanical on 2016-07-17
It means that ASUS do not train their customer support staff about Linux or any distribution of Linux. So, it is no good spending money asking ASUS support on how to install Linux or how to fix any issues regarding drivers. The ASUS support staff have not been educated sufficiently to take that responsibility.

Ubuntu forums is a user forum. Those of us who offer help have been educated in Linux/Ubuntu by our own user experience and by any kind of self-education we can get. 

From a quick look at the specification of that motherboard I will say that there is nothing exotic about the motherboard and there is nothing exotic about the range of CPUs it will take. It does have Intel HD Graphics and Linux comes with Intel video driver modules as standard. 

So far so good. The motherboard will have a UEFI boot system and so you must following these guidelines.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you plan to have Windows on that machine and dual boot with Ubuntu? Are you thinking of re-using a hard drive with Windows already on the drive? What version? It is at this point that things get complicated. Will you install an additional AMD video adapter? Will you be installing a WiFi adapter?

When the machine is built then run a Ubuntu 16.04 live session and test out Ubuntu and test try installing any additional drivers that are needed.

Regards.

---

### Post by Incarnadine on 2016-07-17
:P Welcome to Ubuntu! You'll love it! I'm sure Ubuntu will install smoothly on your new build.

---

### Post by chenjennhaur on 2016-07-18
I am planning to dual boot with windows 10 and do some machine learning with a GTX 1080 card. Not going to install any wifi card. I was just worried if there are any driver issues with tge motherboard. Looks like there shouldn't be any problems. Thanks for the replies

---

### Post by Incarnadine on 2016-07-20
> **chenjennhaur said:**
> I am planning to dual boot with windows 10 and do some machine learning with a GTX 1080 card. Not going to install any wifi card. I was just worried if there are any driver issues with tge motherboard. Looks like there shouldn't be any problems. Thanks for the replies

I was thinking about dual booting as well, but then realized that it would be much easier to just install two hard drives and install Ubuntu and Windows on two separate drives. With this method you don't have to deal with any partitioning.

---

### Post by oldfred on 2016-07-21
With UEFI you do need to be aware of partitioning.
If you only have each drive plugged in during install, UEFI forgets its NVRAM entries for a drive that is unplugged. Often several cold (full power down) reboots will UEFI rediscover entries. Or you can use efibootmgr to add entries.
UEFI fast boot (different than Windows fast start up) skips all UEFI/BIOS checks of system and assumes no changes. It then immediately turns over system to operating system and all system configuration parameters that were previously written on drive are just reused. But that can be so quick that you have no time to get into UEFI to make changes.

With my Asus Z97, I made lots of changes in UEFI settings. And it told me what I changed which I recorded. And update to UEFI version from Asus resets to defaults and you have to change them again.
My Asus had settings for fast boot for both cold & warm boot and sec delay. I turned off fast boot until system was configured and turned it back on for warm/reboot with a 3 sec delay.

---

