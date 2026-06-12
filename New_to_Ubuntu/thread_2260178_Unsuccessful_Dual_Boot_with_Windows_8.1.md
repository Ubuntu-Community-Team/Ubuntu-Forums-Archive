---
title: "Unsuccessful Dual Boot with Windows 8.1"
date: 2015-01-09
forum: New to Ubuntu
---

### Post by Spencer_Workman on 2015-01-09
Model:  Asus zenbook
Original Operating system: Windows 8.1
Processor: Pentium i5 @ 1.7 GHz
RAM: 4.00 GB
Hard drive:  190 GB SSD (w/ 30 GB partition removed) + ~300 GB HDD

I recently attempted dual-booting windows 8.1 with Ubuntu 14.04.1 using the instructions found here {http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html}.  Everything was seemingly going well, as I was able to boot from the bootable USB drive I created and was given the option within the operating system to install alongside windows 8.1 in the 30 GB partition I created and mentioned above.  However, upon rebooting and holding shift, I was given no option to boot into Ubuntu.  I tried to change the boot priorities under BIOS, but no option is given.  I also tried to fix the bootloader from the windows terminal window as instructed in the link I gave.  None of these options worked, and though, under disk management, the partition is formatted as a separate primary partition (and when I try to delete it, windows says it was "created by another operating system"), I am unable to boot into Ubuntu.  

I've been trying this for weeks to no avail and any help would really be appreciated.  I'd really like to get into the open source software and the hacking community, and know this is a necessary first step to doing so.  

Thanks in advance.

---

### Post by ajgreeny on 2015-01-09
As this was a Windows 8.1 machine my bet is that it was using a UEFI system with gpt partitions.

You probably should have followed the details at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") but if you did not do all that was required Boot-Repair in my signature below may get you up and running.

Use a live system to run the boot-info script and post back here the pastebin link you get from that; at this stage don't blindly accept the default repair, just show us the link and somebody will be able to help you out from the info in that.

---

### Post by verymadpip on 2015-01-10
Hi there.
On my (stunningly unsuccessful) dual boot with Win 8.1 laptop attempt I had no grub menu on startup, nor was there an option to change the boot device when I entered the BIOS setup.
What DID give me a useable option was to select the boot device at startup.  That meant pressing the F9 key & not the F10 key.  Your keys will probably be different, as I tried witth an HP laptop.
It's not an ideal solution by any means, but I think it would count as progress of some sort if it works.

I gave up eventually because although I could boot into Ubuntu & use it I could not shutdown or restart the laptop.  It would simply hang.

Good luck sir :)

---

