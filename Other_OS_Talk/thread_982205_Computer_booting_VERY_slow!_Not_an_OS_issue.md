---
title: "Computer booting VERY slow! Not an OS issue"
date: 2008-11-14
forum: Other OS Talk
---

### Post by Fzang on 2008-11-14
My brother's computer boots EXTREMELY slow! The actual OS loads nice and fast (since I just reinstalled) but the it's before the actual boot process...

The first screen that pops up is a BIOS image that tells me my system specs and the "Press F1 for options" and stuff... This dam screen hangs for like 5 minutes before starting to boot, and I don't know what the problem could be

Any help?

---

### Post by Majorix on 2008-11-14
Do you have something bootable-from (doesn't matter what it has on) sticked in? Like a USB HardDrive... Because your PC looks for this kind of stuff before booting.

---

### Post by fwojciec on 2008-11-14
This sort of thing happens on my desktop if my usb audio player is connected during boot.

---

### Post by Fzang on 2008-11-14
The only devices plugged in is audio and a USB mouse... but could they really cause so much trouble? I doubt it

---

### Post by I-75 on 2008-11-14
I was going to say if the printer was connected, disconnect it and see what happens. otherwise go into the bios and make sure that something isn't looking for another drive first like a floppy. 


Also check the RAM, switch them out for another set if you can. Or swap the ram sticks from slot A to slot B. 

 I had a older Dell that would not boot, I took out one Ram stick and then it booted fine.

Another computer would just hang there after booting, I went into the bios and disabled the floppy and the drive for it and no more problems. 

Another computer some time ago would not boot properly, I disabled the printer during the boot process and it booted with no issues.

If none of the above works, go into to the bios again and look at the setup and change if needed.

---

### Post by K.Mandla on 2008-11-14
Some machines have BIOS options for hardware checks at startup; my Inspiron will to a full system profile at every boot if I don't disable it in the BIOS. Doesn't sound like your problem, but you never know. ... :|

---

### Post by smoker on 2008-11-14
enable 'fast boot' option in the bios, which should have post skip the checks mentioned above by K. Mandla. in boot options, ensure the hard drive with the operating system is the first boot option, and ensure this drive is connected as primary master (if IDE drive).

---

### Post by Fzang on 2008-11-15
Alright, I messed around with the boot config.. (no really, all I did was disabling booting from card reader) and now it boots in around... 30 seconds? Woohoo!

It skips the whole hardware check and says "Primary IDE drive" or something and then moves on quickly... odd, "skip hardware check" was already enabled I believe..

---

