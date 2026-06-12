---
title: "Unity - all windows doing slow hip hop across the desktop"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by dogfiresmith on 2014-10-14
Bar on the left, which I think is called Unity.  Downloaded 14.04 from ubuntu.org or .com I forget.  Burned CD, and installed from that.  Lenovo R61 set up to dual boot.

Starts up with 6 pop up windows which say "System problems detected".  No other information.  Everything is in slow motion, any keyboard entry or mouse movements.  And any window on the desktop does a slow motion hopping back and forth.  Slow enough so that I can click on buttons.  

Under the upper right icon for network, nothing is selectable.  So I can't get onto the internet.

Have a hard time getting Windows 7 to start up.  Have to do multiple reboots.  Seems like there is no graceful way of getting out of Unity.  Even using "sudo shutdown -h now", which I got from another post.

---

### Post by Vladlenin5000 on 2014-10-14
Bar on the left is called Launcher. Unity is the Desktop Environment used in standard Ubuntu.

The Lenovo R61 was sold with two different graphics, Intel and Nvidia. Which one do you have in your notebook? They're both old a very limited for any modern 3D DE anyway but one can eventually be improved with proprietary drivers. DON'T expect miracles though.
The Lenovo R61 was sold with 256MB, 512MB, 1GB or 2GB RAM configurations? How much do you have? Anything less than 2GB may not be enough for running Unity, especially when put along a flimsy and old integrated graphics chipset. Other variants with lighter DEs have been suggested in your other threads.
The Lenovo R61 was sold with a variety of wireless cards. Some have native support. Others need drivers or may not be supported AT ALL. Which one do you have?

---

### Post by JeQhdMD on 2014-10-14
I think on this machine, with the dated NVidia chipset, you might be better off installing Mint 17 with the Mate desktop, but, if you use "nomodeset" as a boot parameter, you can get a working (but very slow) desktop thereby allowing you to install the proprietary nvidia driver.   Need to get into "System Settings>Software & Updates>Additional Drivers Tab" & let Ubuntu search for the correct Nvidia Driver.   Once installed, reboot, and you should get a normal Unity desktop - - right now you can't even say there's no graceful way to get out of Unity (as your install is clearly broken).

Re Windows, if you downsized your hdd to make room for Ubuntu, then WIndows will need at least 2 restarts after check disk is auto-run.

---

### Post by Vladlenin5000 on 2014-10-14
I suspect it has the Intel one, not nvidia... The problem is the OP has been asked in several occasions/several threads to post the specs but instead of giving useful information he's been posting the same ramblings all over the place.

---

