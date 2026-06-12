---
title: "triple boot with two hard disks"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bijumgopal on 2008-06-25
Hello,
I am new to the world of Linux.

I bought a 250GB SATA drive to use along with my existing 80GB PATA.
I still want to use the old 80GB PATA with XP because I have some 
video tutorials which I purchased and will only work in that Hard disk with that particular XP version. Further I would like to install Vista and Ubuntu in the SATA drive, thus to have a triple boot system with XP,Vista and Ubuntu on two drives.

I tried several times. Upto Vista it is OK. when I installed Ubuntu
the GRUB is not loading any of the OS. It is not even loading Ubuntu. I am getting error message "Error loading..."
with limited GRUB editing facility, which I am not familiar with.

Definitely it must be a problem with the boot loader. Because before installing Ubuntu everything was fine.

Please advice me.

---

### Post by Canis familiaris on 2008-06-25
If you want to get back XP and Vista boot menu. YOu could remove GRUB:
The easiest but the most expensive (expensive in the sense that you have to burn a blank CD, duh!), you can burn a Super GRUB Disk

You can also use Ubuntu installation CD too:

In the live environment.
Open a terminal window or switch to a tty (Crtl+Alt+F1).
Type &#8220;grub&#8221;
Type &#8220;root (hd0,6)&#8221;, or whatever your Hard Disk + boot partition numbers are.
Type &#8220;setup (hd0)&#8221;, or whatever your harddisk number is.
Quit grub by typing &#8220;quit&#8221;.
Reboot.

However you could also use Windows 98 and Windows XP installer CD
Get Windows 98 boot disk and in the DOS environment: FDISK /MBR
In WinXP installer CD: Go to recovery console and type command: FIXBOOT

---

### Post by Canis familiaris on 2008-06-25
Also then reinstall Ubuntu and in this case when reinstalling Ubuntu:
Create a seperate /boot partition in that PATA hard disk and see whether it works!

---

