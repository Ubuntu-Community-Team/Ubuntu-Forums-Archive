---
title: "Windows 8 not detected"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by Mallika_Agarwal on 2013-09-12
I read threads related to a similar issue, but my issue isn't getting solved. 
I am pretty much a beginner and know very little about everything. 

I am trying to do a native installation of Ubuntu 12.04.3 LTS (64 bit) using a bootable USB on Windows 8. 
I booted from the USB and all, when I get to installation, I do not get the option of "installing Ubuntu alongside Windows". 
I only get:
Erase existing files
Something else 

I have tried running sudo apt-get install os-prober and update-grub as well as boot-repair, but nothing works, I get various errors. 
Help would be MUCH appreciated.

---

### Post by newb85 on 2013-09-12
Have you read the community documentation on UEFI and secure-boot?

---

### Post by oldfred on 2013-09-12
Vital links if UEFI system.
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Also links in my signature which includes above and much more on UEFI.

What system, is it an Ultrabook with RAID and dual video issues in addition to UEFI issues?

---

### Post by Jonathan Precise on 2013-09-12
> In the case of Lenovo you will not have an option to install Ubuntu with Windows 8, the only option is to remove Windows 8 completely.

I hope that your computer is not this one. If it is, you must remove windows 8 to use ubuntu.

---

### Post by oldfred on 2013-09-12
I think every brand has installed Ubuntu, but some are more difficult than others. And a few models in many brands have not worked, but sometimes UEFI/BIOS updates solve those issues.

---

### Post by Jonathan Precise on 2013-09-12
> **oldfred said:**
> And a few models in many brands have not worked, but sometimes UEFI/BIOS updates solve those issues.

Please go [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported") and see the step about UEFI settings:

> NOTE - In the Spanish version of Windows 8, the option for UEFI Firmware Settings is not available in several laptops, tested Lenovo, HP and Acer. They do have an option to boot the computer and another custom menu will appear which lets you do a couple of things. In the case of Lenovo you will not have an option to install Ubuntu with Windows 8, the only option is to remove Windows 8 completely.

Unfortunately, that is the truth with some Lenovo machines.

---

### Post by Mallika_Agarwal on 2013-09-14
newb85: I did, it all seems too complicated for me right now, going for a VMware installation. :/

oldfred: Thanks for the help. And no, it's a Dell Inspiron 15. 

Jonathan Precise: Same as above. 

Anyway, I shall try the help links and get back, for now, I'm closing the thread. :)

---

### Post by oldfred on 2013-09-14
Dell's seem to be similar across models:

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)

---

