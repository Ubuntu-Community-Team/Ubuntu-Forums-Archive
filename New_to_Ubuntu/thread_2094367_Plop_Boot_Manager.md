---
title: "Plop Boot Manager"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by tigman on 2012-12-13
Greetings All,
I recently installed Ubuntu 12.10 Desktop on a 250 Gig, USB Hard Drive using my XP-Pro SP3 laptop (32 bit system).....Installation went fine and it works like a champ.....No problems booting, loading or using.

That said, my next objective is to boot and use my Ubuntu Hard Drive from my desktop computer.....This is also a Windows XP-Pro, SP3, 32 bit system but does NOT have BIOS support for booting from a USB device.

I've downloaded the latest version of "Plop", gone through the prescribed procedure for making the ISO disc and set my desktop's BIOS to boot from the CD-ROM

The ISO file takes over at boot up and I'm presented with a boot option menu.....When I select the "USB" option, the boot loader detects the drive but fails to boot into the LINUX system.

Being a total novice at this, most of the "Plop" documentation is beyond my current level of expertise.....Just wondering if there's something simple I missed here.

---

### Post by COMECON on 2012-12-13
When you try to boot into the Linux drive, does the boot loader give you any errors? If so, please paste them, and we'll try to see what's wrong.

Catbuntu

---

### Post by dannyboy79 on 2012-12-13
so is grub installed on the external usb hard drive? did you use wubi since you mentioned using window xp to create the install. just clarifying what you have done thus far.

---

### Post by tigman on 2012-12-13
> **COMECON said:**
> When you try to boot into the Linux drive, does the boot loader give you any errors? If so, please paste them, and we'll try to see what's wrong.

Catbuntu

None at all.....It seems to detect the drive, try to load then fails necessitating a complete shutdown.

---

### Post by tigman on 2012-12-13
> **dannyboy79 said:**
> so is grub installed on the external usb hard drive? did you use wubi since you mentioned using window xp to create the install. just clarifying what you have done thus far.

Yes it is.....Checked a while ago using my laptop......The GRUB file is right at the beginning of my /boot file.

---

### Post by dannyboy79 on 2012-12-13
instead of plop, try super grub disk live cd

---

### Post by tigman on 2012-12-13
> **dannyboy79 said:**
> instead of plop, try super grub disk live cd

Thanks much......I'll give it a try.....Nothing ventured, nothing gained.

---

