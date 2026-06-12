---
title: "Reinstalling XP"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Benbow on 2008-07-14
Some time ago I removed XP from my system and relied entirely on Ubuntu. I now need to reinstall XP but leave Ubuntu intact is there a way to do this? If this is impossible I will need to take a [COLOR="Black"]comprehensive back up[/COLOR] of my current system including [COLOR="Black"]Firefox favourites[/COLOR], what is the easiest way to do this?

---

### Post by jimmy the saint on 2008-07-14
Use the gparted/clonezilla boot cd to make an image of your disk.  Repartition the drive so that you have one for windows, and one for ubuntu.  install windows on the first partiton and expand the disk image of Ubuntu onto the second.  you may need to mess with grub to make this work, but it is the best way (in my opinion) to keep your current installation, as windows needs to be on the first partition.

---

### Post by nowshining on 2008-07-14
or install XP thru a vm program.

---

### Post by sayakb on 2008-07-14
Download and install VirtualBox: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Install XP on a virtual machine.

---

