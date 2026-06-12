---
title: "HOWTO: Install Ubuntu on SATA, and WinXP on raid on a crappy integrated intel mobo"
date: 2005-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ekravche on 2005-08-28
This is a very dirty solution on how to Install Ubuntu on SATA, and WinXP on raid on a crappy integrated intel mobo that has 4 SATA connectors, 1 IDE connector and 1 Floppy connector. The computer configuration is 2 CDROM drives connected to the IDE connector in a master slave config. 2 HD connected to a raid controller in a master master config. 1 SATA drive connected to the motherboard.

1) Disconnect all drives except the CDROM and the SATA drive.
2) Install Ubuntu from the CD.
3) Disconnected the Ubuntu SATA drive
4) Reconnect The WinXP raid drive.
5) Get Silicon raid drivers on a floppy (It doesn't seem to work off anything else other than a floppy)
6) Start the XP setup, and when prompted to install on a raid device press F6.
7) Once prompted for the drivers insert the floppy, and after the drivers are recognized XP should be able to install to the RAID drives.
8 ) Install XP, but keep all the other peripherals disconnected
9) Once XP is installed, reconnect all the other peripherals and configure the BIOS to boot into the Ubuntu drive first.
10) Then configure the fstab and grub. (see grub config here [http://www.ubuntuforums.org/showthread.php?t=49383&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=49383&page=2&pp=10))

---

