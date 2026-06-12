---
title: "boot manager/loader questions"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by PaulBx on 2013-07-14
I was reading this set of articles about boot managers and loaders:
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

First thing I wonder, is with a standard installation of lubuntu, are we using grub2? I only have lubuntu on this disk so there is nothing to select, but I'd still like to see the menu, which I don't see at the moment (I tried fooling with /etc/default/grub and re-built grub but it didn't do anything). Maybe it flashes by before I can get the brightness turned up in the boot (yeah I have one of those screen brightness problems apparently common in ubuntu).

Second thing is that with a UEFI machine, apparently a boot manager is part of the firmware. And also according to those articles, every OS has a boot loader built right in. So with newer machines I wonder if I can dispense entirely with grub2 (something I'm not fond of anyway) and just use the combination of firmware boot manager and ubuntu boot loader? Anybody tried that?

---

### Post by cariboo on 2013-07-15
To see the grub2 menu, hold down the shift key just after post, and you should see the menu. As for your UEFI question, I can't help you there, as I'm still using a 3 year old system.

---

### Post by oldfred on 2013-07-15
I do not think so.

A Boot Manager just improves the management of the booting process, but is not normally the boot loader. Plus if you need secure boot that complicates things greatly.

I think the rod books site has some discussion on efi stub and some work arounds on various things, but they are all work arounds. That may be converting the efi partition to also be the /boot in effect.

---

### Post by PaulBx on 2013-07-15
Thanks cariboo, I managed to see the grub menu although it was iffy on the timing to press the shift key. At that part of the boot my screen is dark.

oldfred I did attempt using the secure boot but that went nowhere. I will put it on my list of things to investigate later.

If you modprobe efivars you get the efibootmgr command:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

That is something I'd like to try along with the efi stub, to eliminate grub2, if I can figure it out. Or if that doesn't work I might replace grub2 with grub legacy which I understand (sorta). I will look around and report back if I find anything.

<later>
Ah, I guess lubuntu does not yet come out in signed versions which explains why my secure boot failed? Or something...

---

### Post by oldfred on 2013-07-15
Ubuntu has the signed kernels and grub2's shim file. But you have to boot in UEFI secure boot mode to get it to install those versions. Boot-Repair if booted with secure boot will download and install those or you can manually install those versions from command line.

Grub legacy will not work with UEFI and has not been maintained for years, so it is missing large pieces of ways to work with new systems. With 9.04, the last Ubuntu with grub legacy, Ubuntu modified its version of grub legacy to work with ext4. Grub legacy also does not work with gpt partitioning.

---

