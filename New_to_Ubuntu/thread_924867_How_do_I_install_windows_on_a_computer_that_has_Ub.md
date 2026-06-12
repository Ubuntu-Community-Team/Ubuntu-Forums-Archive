---
title: "How do I install windows on a computer that has Ubuntu only?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Warslaughter on 2008-09-20
I have Ubuntu currently installed, and no windows installed, and when i put in the windows boot cd, it wont boot from it.
I was wondering if there was a way i could get windows to install on it's own separate partition other than linux partition and have my computer boot from windows instead of ubuntu on default.

---

### Post by Watchtow3r on 2008-09-20
You're putting the CD in then restarting the computer, right? Also, make sure your boot order (in your BIOS) is set to boot CD BEFORE hard drives. To get ubuntu and Windows, I'd back up all your ubuntu stuff, install Windows to your entire HD, and then use the Ubuntu CD to reinstall it (and Ubuntu easily lets you partition it), then load all your crap again.

---

### Post by Warslaughter on 2008-09-20
yeah, the cd's in the drive prior to me restarting it.

As for booting order in the bios, i didn't do that, but i pressed one of the Fkeys, and selected for the computer to boot from Atapi CD/DVD Rom drive, but it still takes me to the ubuntu start-up screen, where I choose between normal ubuntu or recovery mode

---

### Post by lemmy999 on 2008-09-20
Watchtow3r is totally correct. Windows overwrites the master boot record so it has to be installed first. After that you can re-partition and install Ubuntu with Grub to choose which OS boots.

If you have selected "boot from CD/DVD drive" and its not booting that suggests that your Windows CD is borked! Try it on another machine if possible!

---

### Post by Peter09 on 2008-09-20
If you want windows use virtualbox, its easy and wont damage your Ubuntu installation. (unless you're doing it to play windows games which VBox won't support).

---

### Post by Warslaughter on 2008-09-21
hey lemmy, i'm booting from cd, but it's definitely not the cd's fault, cause i've tried it with 2 different windows 98 SE disk (well same contents but a different cd), and a windows 2003 MCE. None of the cds are burned or anything: the windows 98 disks came with the computer that i had like 8 years ago, and i borrowed the windows Media center one from a friend, and they all have their random windows logos and whatever cover stuff on top.

but for all the cds, it still ends up sending me to the ubuntu boot menu even when i boot from cd.

---

### Post by SunnyRabbiera on 2008-09-21
That is strange, and you say editing the BIOS doesnt work?
what kind of computer is this?

---

### Post by sayakb on 2008-09-21
If you install Windows **after** ubuntu, you'll lose your grub bootloader. Download the Super Grub Disk ([http://supergrubdisk.org](http://supergrubdisk.org)) -- which should be a 4-5MB ISO, burn it to a CD. Now after you have installed windows, pop in the Super Grub Disk and choose to recover GRUB.

---

### Post by kansasnoob on 2008-09-21
This has worked for me more than once:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by kansasnoob on 2008-09-21
> **LinuxIsInnovation said:**
> If you install Windows **after** ubuntu, you'll lose your grub bootloader. Download the Super Grub Disk ([http://supergrubdisk.org](http://supergrubdisk.org)) -- which should be a 4-5MB ISO, burn it to a CD. Now after you have installed windows, pop in the Super Grub Disk and choose to recover GRUB.

Everyone should have a Super Grub Disk! I like Herman's guide:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I have it on Floppy, CD, and USB! It's a life saver!

---

### Post by sayakb on 2008-09-21
Right :) It's really very handy when I lose my GRUB, and thats quite often ;)
PS: Nice guide!

---

