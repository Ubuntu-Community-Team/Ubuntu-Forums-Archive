---
title: "why is wine messing with grub?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-04-17
I was reinstalling wine today because it mysteriously was gone.. I thought that was odd enough, then as I was watching wine 1.4 install, I noticed this

```
Setting up fonts-droid (20101110+git-2) ...
Setting up grub-common (1.99-21ubuntu3) ...
Setting up grub2-common (1.99-21ubuntu3) ...
Setting up grub-pc-bin (1.99-21ubuntu3) ...
Setting up grub-pc (1.99-21ubuntu3) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-3.2.0-20-generic
Found initrd image: /boot/initrd.img-3.2.0-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
Found Ubuntu 11.10 (11.10) on /dev/sdb5

```

why would wine touch my grub files?
just curious is all mostly because I had to reinstall ubuntu 12.04 the other day as my grub files were corrupted, this may be the cause

---

### Post by oldos2er on 2012-04-17
> **beelzebufo said:**
> why would wine touch my grub files?


It doesn't. 12.04 upgrades for today included grub-pc, grub-common, etc., so I'm assuming you ran upgrades concurrently with reinstalling Wine.

---

### Post by beelzebufo on 2012-04-17
negative sir, I ran the update from the updater, then, when that was done, added the wine repo apt-get updated, and sudo apt-get installed wine1.3 (which is the command for 1.4 apparently according to their website

---

### Post by grahammechanical on 2012-04-17
So, you are using 12.04?

It has been my experience that kernel updates have been coming down in two stages or so.

Update manager shows that the kernel is to be updated but the Grub menu does not get updated. The new kernel is not shown in the menu. Then the next update to 12.04 generates the update to grub.

I had this happen to me with the 3.2.0-23 kernel and also on earlier ones. I have several 12.04s on my hard disc.

Regards.

---

### Post by beelzebufo on 2012-04-18
so it continues to update any time apt is used? my question is why when I sudo apt-get installed a specific application did grub get updated.. wine should have nothing to do with grub.  I am just curious at this point

---

### Post by oldos2er on 2012-04-18
> **beelzebufo said:**
>  wine should have nothing to do with grub.

And again, it doesn't. If you post the full terminal output we could probably better advise you.

Edit: apt-get will attempt to configure packages any time it is invoked.

---

### Post by beelzebufo on 2012-04-18
thank you, your edit answered my question

---

