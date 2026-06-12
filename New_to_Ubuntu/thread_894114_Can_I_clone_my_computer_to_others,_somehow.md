---
title: "Can I clone my computer to others, somehow?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by daytonageeks on 2008-08-19
AM using Hardy Heron, have spent the required time setting it up juuuuuust right - now want to clone all my work to other computers instead of having to go through ALLLLL the setup over n over.
Any ideas?
Thanks and Blessings,
                      Daytonageeks (Jim)

---

### Post by nkri on 2008-08-19
You can use PartImage to make carbon copies of your Ubuntu partition, and restore it on as many other computers as you want...but it will only work if the partitions on the other computers are the same size as the one on the original.  For example, if the original is 100GB and the other computer is 50GB it won't work.  If the original and the other are both 100GB, it'll work fine.

Good luck!
-nkri

---

### Post by akiratheoni on 2008-08-19
Perhaps this might help:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by meanburrito920 on 2008-08-19
yes and no. You technically could clone the computer, but it would require fooling your computer into thinking that it had the same specs as the original. The easier option is just to copy over your home directory (which is where all your personal settings are stored). This won't copy your programs over, but it is simple enough to mass install all the same programs. It won't preserve GRUB settings or anything either, but your desktop background, icons, themes, layout, terminal, and most program settings will be the same.

---

### Post by tgalati4 on 2008-08-19
Assuming identical hardware (and I mean EXACTLY the same hardware configuration) you could do the following:

Put the master disk on IDE ribbon 1 and the clone disk (equal or greater size) on ribbon 2.  No need to partition or wipe the clone disk.  Boot from CD using the live disk.  From a terminal:

>cp /dev/hda /dev/hdb

Put the clone drive in the new machine and see if it boots.

I cloned 10 machines this way in a couple of hours.

If you are using SATA drives then you would use /dev/sda.

---

### Post by BLTicklemonster on 2008-08-19
Maybe something like this would help?

[http://ubuntuforums.org/showthread.php?t=852868](http://ubuntuforums.org/showthread.php?t=852868)

---

### Post by Vivaldi Gloria on 2008-08-19
There is NO need for the hardware to be same. Take out the system disk from the ubuntu box and put it in another computer and ubuntu will just work on the new computer provided that:

1) Ubuntu uses a default kernel (you have not compiled a kernel yourself)
2) Ubuntu has no problem with the hardware of the second computer.

When ubuntu boots up it recognizes new hardware and adjusts accordingly.

So first try if the live cd works with the second computer. Then clone the ubundu disk (with e.g. clonezilla) and put it in the second computer.

---

### Post by alienexplorers on 2008-08-19
You could try a program called remastersys.  It lets you make backups of your entire computer or you can make distributation copies.

---

### Post by k3lt01 on 2008-08-19
> **alienexplorers said:**
> You could try a program called remastersys.  It lets you make backups of your entire computer or you can make distributation copies.That's how I do it.

---

### Post by Archmage on 2008-08-19
If you are only talking about your settings in the program:

You could copy your home-partition on the other PC.

---

### Post by daytonageeks on 2008-08-20
I guess I should have been more thorough and clear in my original posting.
This is what I am after:

I want the identical settings and programs to follow from computer to computer.

The hardware will likely be vastly different.

I'm finding myself doing hours of setup on each and I think there must be a way to put all the things that I do post OS install into one package or to slipstream it all into the OS install.

In M$WinXP I used nlite to make this so but am learning Ubuntu as I go along.

BTW, have not rebooted my own machine into M$WinXP for three months and see no need to again except to fix others' computers and to print with my boatanchor Kodak 5100 aio (for which the Linux drivers have, indeed, been developed but are being held from release by Kodak.)

Thanks and Blessings to all who have commented here - am in hopes of figuring this out, with help of this community!
daytonageeks (Jim)

---

