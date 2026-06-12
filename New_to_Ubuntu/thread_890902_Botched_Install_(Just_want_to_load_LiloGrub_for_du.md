---
title: "Botched Install (Just want to load Lilo/Grub for dual boot)"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Hookoa on 2008-08-15
Aloha, I just tried installing kubuntu to my desktop from a CD.  The install froze after the OS installation was completed, but apparently half-way through the bootloader installation.

After searching the web, I couldn't find any suggestions other than to reinstall or try a different distro.

Reinstalling gave the same error (and I think the CD must be corrupt at a certain point), and I don't want to install other distros.

If someone could explain to me how to download either grub or lilo and configure it to give me the dual boot option (windows/kubuntu), I would greatly appreciate it.

I am currently using kubuntu install CD as a liveCD to get me started, but I'd like to use the installed OS.

My devices are

hda
hdb

with windows at hda1
and kubuntu at hdb7
with various partitions for data

Thank you very much for any help.

---

### Post by LowSky on 2008-08-15
[Have you tried an Alternative install CD]("http://releases.ubuntu.com/kubuntu/hardy/kubuntu-8.04.1-alternate-i386.iso")

---

### Post by Hookoa on 2008-08-15
I  haven't tried an alternative install CD because I believe that the kubuntu installation was successful, just not the bootloader installation.  I'd like to try installing that part on this system before I go through the hassles of reinstalling   for what I think should be a fixable problem.

---

### Post by kansasnoob on 2008-08-15
I'll tell you, these multi-drive, multi-boot installations make me crazy. Not so much if I'm doing it myself but it can get fiddly!

First of all if BIOS is set to boot the Windows drive first and GRUB is installed to the the other drive it either doesn't work at all or at best you end up with an incredibly slow boot.

Before I go on you didn't mention if your Windows is XP or Vista. Vista would give you an additional boot option.

---

### Post by Hookoa on 2008-08-15
I have Win XP on hda1

---

### Post by kansasnoob on 2008-08-15
If you want to just try installing Grub, and since I know you have the live CD, look here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or here:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by Hookoa on 2008-08-15
Thank you very much.  I really needed an educated point in the right direction.

---

