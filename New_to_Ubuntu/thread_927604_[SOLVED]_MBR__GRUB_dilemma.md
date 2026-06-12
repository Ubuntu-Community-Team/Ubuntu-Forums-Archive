---
title: "[SOLVED] MBR / GRUB dilemma"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jon555 on 2008-09-23
I had Ubuntu on partition 1, I installed xp on 2nd one. Ubuntu stopped booting. with 
Code:

sudo grub

Code:

root (hd0,5)

Code:

setup (hd0)

Code:

quit

I got ubuntu working, but Xp stopped booting.
with FIXMBR in recovery console I got XP working, but Ubuntu is not booting up any more.:confused:

---

### Post by muteXe on 2008-09-23
Go get the supergrub disk.  Worked for me a treat when xp overwrote my grub.

---

### Post by muteXe on 2008-09-23
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jon555 on 2008-09-23
And what can I do with it? Should I burn it, boot from it or something?

---

### Post by muteXe on 2008-09-23
Sorry was in a rush, it's all on that webby, but yep, burn it to disk (burn the image probably) and boot off it. 
Excellent documentation: [http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by jon555 on 2008-09-23
When I click on download iso mozilla crashes.

---

### Post by livingtarget on 2008-09-23
..or have a look at grub4dos, it's a bit of a hassle to set up if you've never done it before but basically you can boot linux through NTLDR (the windows boot loader)

[https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)

tutorial:
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

or more specific:
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial#Booting_GRUB_for_DOS_via_the_Windows_NT.2F2000.2FXP.2F2003_boot_manager)

---

### Post by bumanie on 2008-09-23
Hi jon555, see you've had some more hassles. Post the output of > sudo fdisk -loff the live cd. It is likely that all you have to do is reinstall grub and all should be fine. Windows has no respect for other OSes and overwrites grub's entry in the mbr.

---

### Post by caljohnsmith on 2008-09-23
Note that if you boot the Super Grub CD, it will give you an option to boot Windows if you use the right menu option. But I assume you don't want to boot the Super Grub CD every time you want to boot Windows, true? If that is the case, you just need to add an entry for Windows in your Grub's menu.lst, and then you can boot Windows from the Grub menu just like you do Ubuntu. If that is what you want, then please post the fdisk command that bumanie asked for, and also post: 
```
cat /boot/grub/menu.lst
```

---

