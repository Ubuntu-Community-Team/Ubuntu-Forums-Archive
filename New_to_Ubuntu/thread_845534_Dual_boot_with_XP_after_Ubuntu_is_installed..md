---
title: "Dual boot with XP after Ubuntu is installed."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Alex Carroll on 2008-06-30
I've been planning to set up a dual boot with XP for a while, and have just created a 40GB partition on one of my hard drives to make space for it. I'm not sure if I can simply run the XP CD and install to that partition without losing anything.

I'd also like Ubuntu to be the default OS, with XP only being an option in the boot loader. However, I seem to remember reading that installing XP after Ubuntu will wipe the Ubuntu boot loader and replace it with the XP one. Is this true, and if so, can I retain the Ubuntu boot loader.

Sorry if the wording is confusing; it's kind of hard for me to explain. Thanks for any help.

Possibly related: Ubuntu is installed on one of my 40GB drives, but the partition I have created for XP is on my 500GB drive. Will this make anything more complex?

---

### Post by jamesrfla on 2008-06-30
Installing Ubuntu then XP will get rid of the Ubuntu boot loader. If you like the Ubuntu boot loader I suggest installing XP first then Ubuntu

---

### Post by WRDN on 2008-06-30
Reinstalling GRUB if it is overwritten by Windows MBR can be very complicated.
After installing XP on the applicable partition, you could use [Super Grub Disk]("http://www.supergrubdisk.org/") to replace GRUB.

---

### Post by Alex Carroll on 2008-06-30
Reinstalling Ubuntu isn't an option I'm afraid; I've been using this install for about 3 months and don't have another hard drive that can accomodate the data I've collected. I can live without the Ubuntu loader as long as I can easily boot into Ubuntu.

Edit: Will the XP boot loader detect Ubuntu and add it to the boot list, or do I have to manually add it?

---

### Post by alzie on 2008-06-30
This site has directions to dual boot ubuntu by adding xp:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

I wouldn't attempt this without backing up as much as possible,  especially any irreplaceable files.  Stock up on cd's or dvd's or check into an online storage site.

Good Luck

---

### Post by jesusprice on 2008-06-30
if you feel lazy and don't want to set up the different partitions just use wubi.

---

### Post by Victormd on 2008-06-30
> **Alex Carroll said:**
> Will the XP boot loader detect Ubuntu and add it to the boot list, or do I have to manually add it?

No, that's the problem. However, you can use [Supergrub]("http://www.supergrubdisk.org/") to reinstall grub or, install windows on a virtual machine.

---

### Post by Paqman on 2008-06-30
> **WRDN said:**
> Reinstalling GRUB if it is overwritten by Windows MBR can be very complicated.


Not really. You just boot up into a LiveCD and tap [a couple of commands](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) into the terminal. Five minute job.

---

