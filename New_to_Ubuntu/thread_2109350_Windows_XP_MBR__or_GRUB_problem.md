---
title: "Windows XP MBR  or GRUB problem"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by bobpur on 2013-01-27
I'm upgrading a dualboot machine I got here that previously run Win XP and Linux Mint 10. I tried Ubuntu 12.10 and it was "buggy." re-formatted the hdd and installed Ubuntu 12.10 again from a different disk. Better (for Ubuntu) but XP wouldn't load from GRUB. It was shown in GRUB menu but when I clicked on it the computer would restart.

Currently have Lubuntu 12.10 installed but XP is still missing. Xp is still there as I can get there through linux and see my pix and stuff. XP will still not load and still restarts when XP is chosen.

Reading back through this before posting it dawned on me that my problem may not be GRUB; but, the MBR in windows. Repairing the MBR through Windows warns against fixing if dualbooting as it may mess up everything. I take it this means overwriting GRUB. 

Need some help guys! Thanks.

---

### Post by mlentink on 2013-01-27
Not sure whether GRUB is your problem. Have you tried running the [boot info script]("http://bootinfoscript.sourceforge.net/")? That would give us valuable details to really dignose the problem.

---

### Post by dchrono on 2013-01-27
I am not suggesting you try any of the following, I am merely letting you know I had the exact same issue. I fixed the mbr in XP first, booted successfully into XP, then reinstalled grub from a live usb and it worked without a hitch.

take this with a grain of salt, I have also read where this same process hasn't worked and both systems lost. I just said the heck with it and tried my luck.

---

### Post by presence1960 on 2013-01-27
> **mlentink said:**
> Not sure whether GRUB is your problem. Have you tried running the [boot info script]("http://bootinfoscript.sourceforge.net/")? That would give us valuable details to really dignose the problem.

What are you waiting for. Without this info we will just be shooting in the dark.

---

### Post by bobpur on 2013-01-28
Sorry, gone most of today and didn't get to do anything. check back tomorrow. family emergency.

---

