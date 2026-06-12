---
title: "Don't know what to select in &quot;Device for boot loader instalation&quot;"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by mcmacker4 on 2013-03-02
I am now trying to install Ubuntu on a Mac. My plan is that when I have it installed I use rEFIt to select the operating system I want to use (Mac OS X/Ubuntu 12.10). An IMPORTANT thing you should know is that I am trying to install Ubuntu in a previously made partition (made with Disk Utility on Mac) IN AN EXTERNAL HARD DISK DRIVE.
But my problem is that, when I'm installing i am asked to select the Device for boot loader instalation and I don't know what to select. I am also worried that I replace the Mac's boot loader with Ubuntu's boot loader, and I don't want that because I don't have the Mac's boot disk. I get 4 options in the instalation process when selecting "Device for boot loader instalation":
-/dev/sda *numbers and letters* (this is the internal HDD)
-/dev/sda1
-/dev/sdc WD*numbers and letters* (External HDD, this is where I want Ubuntu to be installed)
-/dev/sdc1

The question is: What do I have to select?

---

### Post by fantab on 2013-03-02
If you are installing Ubuntu on /dev/sdc (Exteranl HDD) then it will be better to install Ubuntu GRUB (GRand Unified Boot-Loader) on /dev/sdc only and NOT /dev/sdc1 or sdc2 etc. If you install it on /dev/sda (which I assume is your Mac) then Grub will overwrite the Mac bootloader. I don't use Mac so I am not sure if rEFIt will detect Ubuntu or not.

If for some reason rEFIt is not able to boot Ubuntu then you should look in BIOS or whatever and tell it to boot USB devices first (assuming your External HDD uses USB), so when ExHDD is connected your BIOS will boot it first if not you will boot into Mac.

Good Luck....

---

### Post by mcmacker4 on 2013-03-03
Ok, I did so, But now I get a message that tells me "No root file system is defined. Please correct this from the partitioning menu." and I don't know hat to do... What do I have to do?

---

### Post by fantab on 2013-03-03
Use Gparted (Disk Management Utility) in your install CD/USB to partition your ExHDD or use the similar Mac utility (recommended).

Make a 15-20 GB partition to keep your 'System Files'. During Install you will have format this partition as EXT4 and select "/" as your mountpoint.
Make 2-4 GB partition and format it as "SWAP" or "Linux SWAP" during Installation. If you hibernate your machine then make this partition a little bigger than you RAM-Memory.
Make (As big or small as you like) GB partition and during install format it as EXT4 and select "/home" as mountpoint (This partition is where you will be storing all your user data).

More Info:
[http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu](http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

Good Luck...

---

### Post by mcmacker4 on 2013-03-03
I di all this, but now my problem is that the computer is stuck at "Detecting file system..." (just after giving login info) and it does nothing...  Is this normal?

---

