---
title: "Laptop instal hangs"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Jamface on 2008-07-01
I have installed Hardy Heron successfully on my PC but cannot do so on my laptop.  When I run the disc from the CD/DVD drive I get as far as the instal options screen, a flashing '-' cursor appears after I select option 1 (run from CD), the drive is active for about 1 minute then stops and the machine hangs - nothing will work.
Any thoughts on this problem?
What else would you need to know to help with it?
The laptop is a Sony PCG-FX109K which I have upgraded from 250 to 500 kb RAM and an 80GB HD with 70GB free space.  The processor is a mobile Intel Pentium III 850 MHz.  The CD/DVD is a Mashita UJDA710.
The machine runs Windows XP with SP 2 with no problem - apart from it being Windows!
I have not previously tried to run or install Ubuntu on this machine.

---

### Post by Ryadt on 2008-07-01
you probably will need to install using the alternate cd.

---

### Post by sayakb on 2008-07-01
Do a text mode install using the Alternate CD or use "Safe graphics mode" with the LiveCD.

---

### Post by Rope on 2010-07-06
Hello,
I know this is a long time ago, but these days I wanted to install xubuntu 10.04 on a sony vaio pcg fx109k and I did experience the same problem. (I did try ubuntu and xubuntu 9.04, 9.10, 10.04)


After some googling and trying and trying I managed to install a xubuntu 10.04 on this old laptop. Just wanted to let you know out there...

First: acpi must be off, as mentioned in another thread ([http://ubuntuforums.org/showthread.php?t=429477&highlight=pcg+fx109k](http://ubuntuforums.org/showthread.php?t=429477&highlight=pcg+fx109k))
I did not find any other way (no wlan?)

ok:
0) you will need another screen (see 2nd point)
1) start with live cd, press F6, select acpi=off
2) as soon as x starts, the screen will flickering, i think with x in failsafe mode it would work, but this option is gone... (last seen in 9.10). So I connected another TFT, so it works.
3) install xubuntu with no problem
4) restart after install will lead in grub error: "error: no suitable mode found, error: unknow command 'terminal'"
5) we will need to change some grub options, so restart laptop with live cd
6) F6 -> acpi=off and start live cd without installing
7) after boot up, open terminal, become root with 'sudo -i'
8 ) mount your system harddisk:
8a) mkdir /media/disk
8b) mount /dev/sda1 /media/disk
9) prepare for chroot and do chroot
9a) mount --bind /dev /media/disk/dev
9b) mount --bind /sys /media/disk/sys
9c) mount --bind /proc /media/disk/proc
9d) chroot /media/disk
10) now our root is on the system harddisk, any change you make in here is on the installed version. Ok, now we will change the grub settings:
10a) open /etc/default/grub with nano: nano /etc/default/grub
10b) go to the line where the boot options are listed: something like "quiet splash". Modify the boot options to be like: "quiet splash acpi=off i915.modeset=1", save and quit nano
10c) execute: update-grub
11) restart your laptop
12) now xubuntu should boot, but remember, we still have the additional screen connected. If we disconnect the additional screen and do a reboot we will still have the flickering 800x600 image, instead a 1400x1050 screen.
13) for this we must have a (faked) /etc/X11/xorg.conf (in default install we do not have anyone). Ok, copy the existing failsafe one: cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
14) if you restart your laptop with this, the screen will be readable (not flickering), but will have 640x480 only. What I did to get a better xcorg.conf
14a) connect the other screen, modify the xorg.conf to have an invalid one (say delete all except the 'Screen' section
14b) reboot, there will be an error message saying that ubuntu runs in a too slow resolution -> select stop this and go to terminal.
14c) execute: Xorg -configure
14d) copy the new xorg.conf from /root: cp /root/xorg.conf.new /etc/X11/xorg.conf
14e) disconnect the other screen and reboot
15) xubunutu should boot (notice the grub error (no suitable mode) is still there, but it boots). x should start with a better resolution.
16) in the xfce settings for the screen I was able to select the correct 1400x1050 mode now.

Note: No guarantee!
Thanks to community for all these tips I found around the world...

---

### Post by Jamface on 2010-08-28
Many thanks, Rope.  I have just seen your detailed post.  I'm still working on trying to install Ubuntu on this machine after leaving it for some time.  I'm going to try the alternate CD when I can get Windows XP to burn the ISO image to CD.  Your suggestions look good, but I have quite a bit of learning to do before I would be confident to try them all.

---

