---
title: "not booting after installation"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by blairbeckwith on 2008-08-29
Hey guys;

I just installed kubuntu as my primary operating system on my PC.  Installation went fine, with no problems, until I tried to boot.

The kubuntu blue booting progress bar logo screen thingy comes up, and that goes by with no problems.  Then, it switches to a weird console-like view, with a whole bunch of text, and it just seems to go on for ever.  Here is a sample of the text:

> [ 2318.207982] ata5.00:   status { DRDY }
[ 2318.501720] Buffer I/O error on device sda, logocal block 3
[ 2348.452594] ata5.00: exception Emask 0x0 SAct 0x0 SERR 0x0 action 0x2 frozen
[ 23.48452640] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma **4096** i

(initramfs)_


The 4096 is the only number that really means anything to me, and even then, not really. 4096 is a common amount of ram, but I only have 2048 mb.  The above text repeats, with the numbers on the left hand side (xxxx.xxxxxx) keep increasing.  I figure I'll let them reach 4096 and see if that does anything.

Anyone have any ideas?  Windows XP booted fine (albeight very slow) on this machine.

---

### Post by swoll1980 on 2008-08-29
> **blairbeckwith said:**
> Hey guys;

I just installed kubuntu as my primary operating system on my PC.  Installation went fine, with no problems, until I tried to boot.

The kubuntu blue booting progress bar logo screen thingy comes up, and that goes by with no problems.  Then, it switches to a weird console-like view, with a whole bunch of text, and it just seems to go on for ever.  Here is a sample of the text:




The 4096 is the only number that really means anything to me, and even then, not really. 4096 is a common amount of ram, but I only have 2048 mb.  The above text repeats, with the numbers on the left hand side (xxxx.xxxxxx) keep increasing.  I figure I'll let them reach 4096 and see if that does anything.

Anyone have any ideas?  Windows XP booted fine (albeight very slow) on this machine.

I don't know for sure but try going to your BIOS and disabling your floppy as a boot option I've seen similar problems that were solved by doing this

---

### Post by blairbeckwith on 2008-08-29
About ready to quit and destroy my computer. 

The console window thing is called BusyBox.

---

### Post by Daveski on 2008-08-31
This can happen if the CD you installed from has an error. Best to check the CD and/or burn a new one at a slow speed.

This definately looks like the installed OS is somehow not able to read the main boot partition which could be a hardware failure (or potential failure).

You could try:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

If this does not work, try **all_generic_ide** instead of **noapic**

See these threads:
[http://ubuntuforums.org/showthread.php?t=854618](http://ubuntuforums.org/showthread.php?t=854618)
[http://ubuntuforums.org/showthread.php?t=844288](http://ubuntuforums.org/showthread.php?t=844288)

---

