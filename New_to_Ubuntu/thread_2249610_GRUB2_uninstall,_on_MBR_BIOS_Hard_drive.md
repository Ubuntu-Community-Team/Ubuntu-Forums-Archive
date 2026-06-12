---
title: "GRUB2 uninstall, on MBR? BIOS? Hard drive?"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by gabe2 on 2014-10-23
Some time ago I installed Ubuntu on a second hard drive and set up my machine to dual-boot and it worked nicely. I decided that I didn't really use Ubuntu much and it wasn't compatible with some hardware that I had, so I uninstalled it and tried to set everything back to the way it was before. I'm 99% there. My only beef is that when I start up my computer, it takes quite a bit of time for the OS to load in BIOS before getting to the Win7 splash screen. It's where normally the system reads GRUB2 and then I get into the purple dual-boot screen to choose my OS, but now it is correctly just booting straight into Win7. The issue is that it seems like it's still reading like GRUB2 is there, even though I'm pretty sure I removed it (repaired & rebuilt BCD, even).

As it is, however, I bought a newer, faster, and bigger hard drive to do a fresh Win7 install into and should be getting it any day now. I'm hoping this will resolve the issue.

The main question is this: is the GRUB2 loader in the hard drive or is it somewhere on my motherboard in BIOS? It shouldn't be, right?

Thanks in advance!

---

### Post by irv on 2014-10-23
When you install the new hard drive it will only have Windows 7 after the install. It will fix your master Boot Record (MBR) on install. No more Linux or Grug2. Your grub is loading from your Hard Drive from the boot sector.

---

### Post by grahammechanical on 2014-10-23
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

_Grub version 1 (legacy)_

> [COLOR=#252525][FONT=sans-serif]The master boot record (MBR) usually contains GRUB [/FONT][/COLOR]*stage 1,*


_Grub version 2_

> **Stage 1: boot.img is stored in the master boot record (MBR),**


Did you disable quick boot/fast boot in BIOS?

Regards.

---

### Post by gabe2 on 2014-10-23
Ah, many thanks. As for quick boot, I can't remember, I'd have to go into my BIOS and take a peek. I have to reset it back to default anyway for the new hard drive.

I did some Googling and found this: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I'm posting this for anyone else who might be running into the same problem as I am.

---

