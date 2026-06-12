---
title: "Installation issues resulting in PXE error"
date: 2017-10-24
forum: New to Ubuntu
---

### Post by chiggs88 on 2017-10-24
First off, I'm brand new to Ubuntu and Linux in general, coming from years of Windows and MacOS.

I'm attempting to install the current Ubuntu LTS via USB on a Lenovo IdeaPad V570 which admittedly gave me more issues than I wanted. I managed to reach the point of the install where it prompts me for a reboot after completion. Upon rebooting though, I'm struck with a 'PXE-E61 Media Test Failure' which prompts me to check cables. and then loops into selecting which device I want to boot from perpetually.

Admittedly this is a first for me and I'm not sure how to progress from here.

Any help is greatly appreciated, thanks in advance. Please let me know if I can further clarify any issues I'm having.

EDIT: Problem solved. The issue I was having was that, apparently, GRUB2 does not play nicely with EFI partition tables. To fix this, I had to load into a Live instance of Ubuntu, open Gparted, unmount all the partitions and swap, format the drive, and set a new MBR/MSDOS partition table. Then, I had to reboot back to the Live USB selection menu, choose install Ubuntu, and manually set that partitions so it would keep the MBR partition table. Afterwards everything worked just fine! Hopefully this is helpful to someone else who has the same issue.

---

