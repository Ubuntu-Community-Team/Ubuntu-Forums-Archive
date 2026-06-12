---
title: "Dual Boot required ??"
date: 2016-03-15
forum: New to Ubuntu
---

### Post by Bewildered_Bob on 2016-03-15
Win 7 is already installed and working properly. Ubuntu 14.04 has been successfully loaded to HD (i think). But during boot-up there is no prompt asking which OS shd be loaded. Is there a dual-boot option somewhere that has been overlooked ?  If so, where are install instructions ? Thanx.

Bewildered Bob

ps: how can the installation of 14.04 be confirmed ?

---

### Post by oldfred on 2016-03-15
From live installer:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Geoffrey_Arndt on 2016-03-15
Also, from the Live Disk (or usb-stick), run the program "gparted" and look at your PC's partitions.   You should be able to see all of them using the drop-down in upper right corner.     Seems like you may have borked your install . . . where did you tell the installer to put the bootloader file (grub2)?   Normally best to install it to "sda".

---

### Post by Edward_Fish on 2016-03-16
Something like this happened to me. This worked for me:
Turn off your computer, then turn it back on again. Before the Windows boot screen appears, you should see a message saying something like: *Press F10 to enter setup. Press F2 to select boot device.* Press the key to select boot device (it is probably not F2). A menu should appear with options like: *320 GB ATA HDD WINDOWS, UBUNTU, BOOT FROM EFI FILE, CD ROM DRIVE, USB DISK, NETWORK BOOT.* Use the arrow keys to highlight Ubuntu and press Enter/Return on the keyboard. Now, either Ubuntu or GRUB will load. If GRUB loads, select Ubuntu from the menu like before.

You can confirm that Ubuntu was installed correctly by booting a live CD/DVD/USB, opening the dash, and launching an application named *gparted*.
**BE VERY CAREFUL! PRESSING THE WRONG BUTTONS HERE COULD ERASE YOUR DISK!**
Don't push anything, except to close pop-up boxes.
Look at the colourful bar. If Ubuntu installed successfully, you should see lots of little bars (boot, swap and recovery partitions) a big bar close to the left (Windows) and a big bar to the right of Windows (Ubuntu).
If there is just one big bar (Windows), go run the installer again. (Oh, and close gparted, lest you hit something by accident.)
When you get to the screen that asks:
- Install alongside <xyz>
- Erase disk and install Ubuntu
- Something else
<xyz> should read "Windows Z" if Ubuntu is not installed and "Windows Z and Ubuntu XX.YY" if Ubuntu is installed.
Hope I helped :)

---

### Post by Bewildered_Bob on 2016-03-16
THANX to all who responded.  Bug was caused by operator error - the existing HD partition must first be "shrunk" to make space for Ubuntu. No err msg appeared to indicate that this important step had not be done first.

Bob

---

### Post by Dixie_Lou on 2016-03-18
Hey you with the OPERATOR ERROR,,,I fight that all the time.

---

