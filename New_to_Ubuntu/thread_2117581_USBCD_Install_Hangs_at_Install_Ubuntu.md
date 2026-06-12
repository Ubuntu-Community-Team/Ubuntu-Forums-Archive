---
title: "USB/CD Install Hangs at Install Ubuntu"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by con7undrum on 2013-02-18
Having difficulties installing to an actual hard disk.

System
--------------
MB: Sabertooth Z77 (Ubuntu Friendly - w/ Latest BIOS)
Video:  ATI Radeon 78xx
Memory: 16GB
Proc: Intel i7 3770K

Ubuntu Version(s)
------------------
12.10 Desktop x64
12.04 Desktop x64
12.04 Alternate x64

Symptoms (for all media types above)
--------------
Attempts to boot from CD/USB (UEFI) present base menu (e.g. Install Ubuntu, Test Memory, etc.) but hangs after "Binary Whitelisted".  It just goes to a black screen.

Attempts to boot from CD (non-UEFI) allows me to get a little further.  I can select a language and get to the Install Ubuntu/Check disc for defects/etc.  When I hit enter on install Ubuntu it looks like it's going to work, and then goes to a black screen.

Troubleshooting
------------------
I can't get to any logging (that I know how to get at).  I've tried removing all disks and going back to a default load on the motherboard BIOS.  I've disabled the Secure Boot mechanism (no effect either way).

Using the CD (non-UEFI) I can enter other kernel options and I've tried checking off acpi=off & nomodeset (looking through the forums I found similar suggestions though slightly different circumstances).

ISOs are good (I can use them to build VMs all day long)
Images written to USB via dd, USB Creator, UNetBootin and to CD via InfraRecorder.

I'm just at a loss on where to begin troubleshooting further seeing as I can't get in to anything to troubleshoot.

Thoughts?

---

### Post by Asatru9 on 2013-02-19
UEFI seems to be causing a lot of trouble recently.  I would suggest reading threads (via searching the forums) that have problems dealing with that in general and you hopefully will stumble upon an answer for your question.  Do a web search using keywords like "Ubuntu+UEFI" and see what shows up.

I can't be more helpful due to me not having issues with UEFI but I hope that at least can give you a place to start!  I am the same way I wish people could say do this and type that and reboot but this sounds like a problem you are going to have to dig a bit for the answer.

Good luck!

---

### Post by con7undrum on 2013-02-19
Found the fix...

First - I was able to get the Ubuntu loader to output verbose by removing the 'quiet' from the grub boot string.

Once I did that, I was able to see where the boot was hanging.  My search criteria for "The Book of Knowledge" was:

 "failed command: identify packet device"

Which lead me to this link ([http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device)).

It just so happens that my Sabertooth Z77 sports an ASM1061 SATA Controller and it just so happens my CD-ROM is plugged into it.  Swapping it to another port handled by another controller fixed the issue.

TL;DR - Switching my optical drive to a port managed by a different SATA Controller resolved the issue...

---

