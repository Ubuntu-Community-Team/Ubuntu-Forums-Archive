---
title: "[SOLVED] Ubuntu 8.04.1 Freeze"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by olddavd on 2008-11-17
I'm a noobie with Linux and having extreme trouble getting Ubuntu to load and run. Sometimes I can install 2 or 3 times and get it installed. Usually within minutes the system completely freezes. ctrl-alt-backspace does nothing and have to reboot. I've tried 8.04.1 64 bit the 32 bit will not load period. Zubuntu will install but freezes hard within minutes just like Ubuntu. System information:
AMD Atholon 64 3400+ 2.41 Ghz with 1.0 GB memory
Radeon 9250 
Samsung SVG2001H 20GB hard drive
ST31200264s SATA 120 GB hard drive 
Optiarc DVD RW AD-7170A

Tried the memory test for 12 hours with no problems. Don't know how to test the video card.

---

### Post by nhasian on 2008-11-17
these bootable CDs have diagnostic tools to test various hardware in your computer:


[http://www.livecdlist.com/?pick=All&sort=&showonly=diagnostics](http://www.livecdlist.com/?pick=All&sort=&showonly=diagnostics)

---

### Post by olddavd on 2008-11-18
Thanks for the info nhasian. I tried the UBC. None of the diagnostic tools showed any problems. I am using the Windows install on the second (IDE) hard drive. The disk check function show that the CD is okay. I'm currently downloading the alternate disk image for the 32 version of 8.04.1. Maybe it will install. Tried running the 32 bit from cd for a short while after changing the sound to alsa without issue. Any futher ideas?

---

### Post by nhasian on 2008-11-19
wow that 20 gig hard disk is still good huh?  I'd be pretty skeptical of it. hehe

If your system is freezing check to make sure your:

[LIST]
[*]IDE and SATA cables are in good condition.
[*]motherboard has the the lastest firmware update for the bios
[*]Fans inside pc are spinning & CPU's heatsink is seated properly
[/LIST]

---

### Post by growingneeds on 2008-11-19
Hi,

Your CPU is of the AMD64-type. Please check that you are using an ubuntu installation such as the following:

ubuntu-8.10-alternate-amd64.iso
ubuntu-8.10-desktop-amd64.iso
ubuntu-8.04.1-alternate-amd64.iso
ubuntu-8.04.1-desktop-amd64.iso

If the "desktop" install does not load properly, your best bet will be the "alternate" install. It's text-based, and demands little of your video card. Please also ensure that you are installing onto the newer hard drive. A lot of times, the install fails because the hard disk is reaching the end of its lifespan.

Also perform an integrity check of your installation CDs.

---

### Post by olddavd on 2008-11-19
Thanks to everybody that has helped. I booted the live cd in safe graphics mode and ran for over an hour without a problem (Ubuntu 8.04.1 32 bit version). Think this means the issue is the video card so I will install and run with vesa.

---

