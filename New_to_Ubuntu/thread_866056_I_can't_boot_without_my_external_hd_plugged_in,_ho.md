---
title: "I can't boot without my external hd plugged in, how do i change the grub drive?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by nappymonster on 2008-07-21
Hi all,
I need really really thorough instructions on how to change the drive that grub is installed on. Currently when i boot, I can only boot into anything if:
-My BIOS is set to internal
-My External drive is plugged in

I want to change it so that i can unplug my external drive and boot into windows vista, and plug in my external drive, set the bios to external and be able to boot to ubuntu.

The instructions don't need to be in-depth until we start doing anything on the linux/mbr/terminal side of things. I'm happy to burn any iso's needed. 

I think my issue is that grub is on the wrong drive, but i'll let you experts decide the issue, and, more importantly, how to fix it!

Thanks,
Nappymonster

---

### Post by Potatoj316 on 2008-07-21
It sounds like GRUB in on your external HD and im guessing this is because you installed ubuntu to the external drive.  My recomendation is to back up your menu.lst file (path /boot/grub/menu.lst) and reinstall GRUB using the ubuntu live CD.  After you install GRUB then you can examine the backed up menu.lst you can transfer some of the menu entries from the back up to the new one.

---

### Post by nappymonster on 2008-07-21
There is absolutely no reason why i would have to re-install ubuntu - it's something to do with grub super disk, i'm just not sure how to properly use it.

---

### Post by NilsE on 2008-07-21
> **nappymonster said:**
> There is absolutely no reason why i would have to re-install ubuntu - it's something to do with grub super disk, i'm just not sure how to properly use it.I don't think the suggestion was to reinstall Ubuntu but to use the LiveCD to reinstall GRUB..

An alternative is to use the Windows utility for restoring the MBR on the internal drive so GRUB is not needed for it. Then you can set your bios to boot from the external when it is present and it should default to the internal when it is not.

---

