---
title: "No desktop upon new install of 12.04 (hp pavilion dm1)"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Pavonis on 2012-12-09
I installed a 64-bit 12.04 Ubuntu on a new hp pavilion dm1 laptop. After a fresh install, the boot failed at a Purple Screen of Death. I then used recovery mode to edit grub, replacing "quiet splash" with "nomodeset" and now can get a command prompt. But no desktop. What am I doing wrong?

lspci returns for VGA,
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9808

---

### Post by Bashing-om on 2012-12-09
Pavonis; Hi !

You are probably doing nothing wrong, but lets look at what haps:
boot up to that command prompt; login and enter password; then terminal command:
```
sudo start lightdm
``` to start the GUI desktop.
Please advise of results and post any errors.
[INDENT][INDENT]just try'n to help <==BDQ

[/INDENT][/INDENT]

---

### Post by Pavonis on 2012-12-09
output of sudo start lightdm:

fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
/dev/sda2: clean, 163694/30285824 files, 2655466/121129472 blocks
/dev/sda1: 3 files, 118/95491 clusters
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                  [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFM
/dev/sda2: clean, 163694/30285824 files, 2655466/121129472 blocks
/dev/sda1: 3 files, 118/95491 clusters
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                  [OK]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned                    [OK]


....

And then it just froze

---

### Post by Bashing-om on 2012-12-09
Pavonis;

The output is normal bootup dialog, just not activating X. Lets see if this works:
Boot back up to the grub menu and reinsert the terms "quiet splash" and add "radeon.modeset=0" rather than "nomodeset"; ctl-x to continue the boot process.


[INDENT][INDENT]fingers crossed and awaiting<== BDQ

[/INDENT][/INDENT]

---

### Post by Pavonis on 2012-12-09
Okay, now I see the purple loading screen with Ubuntu logo for about 1.5 seconds and then it dumps me back to command line.

But "sudo start lightdm" now returns different output:

> 
... (lots of stuff with [OK] )
* Starting CPU interrupts balancing daemon [OK]
* Stopping anac(h)ronistic cron [OK]
and then it freezes. I can't ctrl-c out or anything.

---

### Post by Bashing-om on 2012-12-09
yuk.. ok ..lets back up to basics. Can you boot up the install cd into the "try ubuntu" mode?
We are going to boot from the cd, not from the install hard drive,; set boot priority to boot cd first.
But, rather than booting up straight to ...hold the shift key when bios screen clears->language screen ->escape key to accept the default ->boot options screen;
f6 key gives some options, try them and see if any work to boot to the desktop (f10 key to continue the boot process)

What are you looking like now ? <== BDQ

---

### Post by Pavonis on 2012-12-10
I gave up on 12.04 and installed 12.10 instead.

It works perfectly.

Regardless, thank you so much for your help!

---

### Post by mlentink on 2012-12-10
Jumped in just a minute too late. I'm typing this on a HP dm1, and found it a bit odd that 12.04 did not work, as it did on mine. 
12.10 is better though.

---

### Post by Bashing-om on 2012-12-10
Hate to say I do not know, real bad response. Hp traditionally plays nice with linux('buntu) !

Anyway, the important thing is you have an operating system.

[INDENT][INDENT][INDENT]Happy ubuntu'n <== BDQ

[/INDENT][/INDENT][/INDENT]

---

