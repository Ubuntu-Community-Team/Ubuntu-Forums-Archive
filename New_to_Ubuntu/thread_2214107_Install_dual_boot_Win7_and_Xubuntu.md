---
title: "Install dual boot Win7 and Xubuntu"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-03-30
Ok, two scenarios :
1 - Desktop with two 500 gb hard drives
2 - Laptop with one 500 gb hard drive

On both machines, Win7 64-bit is installed, which means one whole partition is taken up on the laptop, second HDD on the desktop free (identified as SDA by xubuntu live).
What's the best way to install Xubuntu in addition to win7 on both the desktop and laptop respectively ?

---

### Post by Chessgeek2900 on 2014-03-30
Greetings.

When I was trying to figure out how to get linux on this machine (it seems so long ago, yet it hasn't even been a week yet!) I remember reading something about doing dual-boot with Windows.  I believe that can be done using a bootable dvd or USB drive--let me do a quick search to double-check my memory...  Yes, here we go.  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  I used this as a general guide, though it involved a lot of trial and error before I could create a bootable USB drive (in the end, I used Unetbootin to make it bootable.  The computer I used to download Linux and create the bootable USB drive is pretty old, and not very fast.)  From that point, you need to configure your computer's boot options to boot from USB (F2 on my computer, F10 or F12 on some others--watch for something saying "boot options" when you turn your computer on.  It should be at the bottom of the screen before Windows loads.)  Once it boots from the USB drive, you should get a menu with several choices on it.  These include starting linux from the USB drive (a trial mode, if I remember correctly) and installing Linux.  I do not remember for sure, but one of these options may be to install it to dual-boot with your current operating system.  If the option is not on that screen, then it is almost certainly on the following one, when you begin configuring your installation of Linux.

There is a specific guide somewhere for the dual boot with Windows setup (when Windows is already on the computer,) but, unfortunately, I do not remember where.


I hope this helps!

Chessgeek2900

---

### Post by Mark Phelps on 2014-03-30
What I would recommend in the two-drive system is to keep the drives separate, with one OS for each drive.  That allows each drive to be bootable on its own and also prevents accidentally corrupting either filesystem when updating the other.  

To do this with your setup, do the following:
1) Have only the Ubuntu target drive connected to the desktop
2) Install Ubuntu, using the entire disk
3) Reconnect the Windows drive -- but  continue to boot from the Ubuntu drive
4) Reboot into Ubuntu
5) Open a terminal and enter "sudo update-grub".  This will regenerate the default GRUB config file and add an entry for Windows.

When you reboot, you'll see a GRUB menu with entries both for Windows and Ubuntu.

One the one-drive system, there are more steps as making a backup is important to be able to restore the working system.  There is also the possibility of the drive already having the maximum of 4 partitions.  Dual-boot prep instructions are the following:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Dr. McKay on 2014-03-31
Thx !

---

