---
title: "[SOLVED] Windows reinstall"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Metal Mick on 2008-07-14
Hi all,

I have Ubuntu installed (via Wubi) on drive E on my machine, and Windows on drive C. I keep all my data on a separate hard drive, so losing that is not a concern.

I need to do a reinstall of Windows (XP), and would like to know the best way to proceed. I do not want to do a reinstall of Ubuntu, because I'd added a fair bit of software and some drivers and just don't want to repeat the process again. (Windows will be bad enough...)

There is an install item under the system menu in Ubuntu, and if this simply transfers my Wubi install to a "regular" install, then I am pretty much good to go, because I am quite confident I can manage the config of the boot loader by myself once Windows is back up and running.

Would love to get some advice on how to achieve my goal, and any thought will be gratefully received.

Regards,

Michael P

---

### Post by echo314 on 2008-07-14
I think your on the right track. If you are reinstalling Windows, you will have to transfer your Ubuntu install to its own partition. Then you can install Windows, taking care to only install over the free space.

Once you have installed Windows, however, its boot loader (Windows now, instead of GRUB) will totally ignore any Ubuntu partitions you might have. Read up on setting up grub in a situation like this (which should not be that uncommon, but I can't find a link right now.)

---

### Post by arpanaut on 2008-07-14
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

This should give what you need to know to accomplish what you describe.

---

### Post by Metal Mick on 2008-07-20
HI all,

many thanks for the help and suggestions, but things did not go quite as I hoped.

To recap, my windows is on drive C (or Hd0), and I had Wubi on HD1 (main partition) and as per advice, downloaded and installed LVPM and transferred my Wubi to a (primary partition) on a third HD.

After uninstalling Wubi form within Windows I cannot boot into Ubuntu.

I have fiddled for several hours with SuperGrub, to no avail. For some reason I find real problems with the syntax of SG and struggle to do anything with it.

I still have my WinXP, and am posting from within that OS.

Can someone help me get GRUB (or similar) up and running so I can get back to my rightful OS? <smile>

Regards,

Michael P

---

### Post by Metal Mick on 2008-07-21
Hi everyone,

it seems I have some form of truce with SuperGrub! I have managed to get booting back into Ubuntu working again.

Many thanks to those who helped me migrate.

Michael P

---

