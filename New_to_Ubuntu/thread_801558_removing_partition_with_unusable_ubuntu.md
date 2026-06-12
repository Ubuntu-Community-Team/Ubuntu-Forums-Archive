---
title: "removing partition with unusable ubuntu"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by adamgram on 2008-05-20
I installed Ubuntu 8.4, then followed some instructions to upgrade the software to Ubuntu Studio.  Now when I boot up I have 3 options: Ubuntu rt, Ubuntu generic, and Windows XP.  Recovery partitions are on the list as well.  If I boot in Ubuntu generic everything works fine, but if I boot in Ubuntu rt (which is the default if I'm not in front of the computer to choose the other option), the mouse will move but can't click on anything and I can't open any applications.  

I'm not sure where the other partition came from or why it dosen't work, and it's probably a stupid question about how to get rid of it, but nonetheless I'm not sure.  Thanks for your help.

---

### Post by Paqman on 2008-05-20
You can remove it from the Grub menu by editting /boot/grub/menu.lst. Just comment out anything you don't need by putting # at the start of the line.

While you're there you can see which partition it corresponds to. Grub numbers from zero, so what Grub calls hd0,0 (hard drive 0, partition 0) would be called sda1 elsewhere (and hd1,2 would be sdb3, for example). If you're sure which partition it is that you don't need, boot up into the LiveCD, open up Gparted, delete the partition and expand the others into the newly freed space.

Of course, you don't have to delete it. Having a spare partition can be handy if you want to try out another distro at some point.

---

### Post by adamgram on 2008-05-20
Perfect!  I just took it off the list, now I don't have to wait for the screen when it boots up!  Thanks!

---

