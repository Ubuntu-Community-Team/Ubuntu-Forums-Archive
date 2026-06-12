---
title: "win 7 dual boot with lucid"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by karrank% on 2011-09-29
Just got a copy of win 7 (please don't throw stuff:redface:) 

Here's the deal--already have a decent enough install of Lucid on my home-built box.

Seem to recall the general wisdom ca 2006 was to install Win first then Ubuntu. 

Does this still apply in these modern times?

Just one box in the house, three users, all accustomed to dual boot environment/grub intro screen in the past, so thinking this is the best way to proceed. 

Any thoughts?

Thanks for looking.

---

### Post by 3177 on 2011-09-30
I'd say back up all your stuff.
you obviously have a win7 cd so you can try try and try again.
windows probably will destroy grub, but you can just re install it via a live cd.
good luck:p

---

### Post by wildmanne39 on 2011-09-30
Hi, it is still best to install windows first but here is a guide to install windows after.
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
The guide is a little old but the procedure is the same.
Thank you

---

### Post by oldfred on 2011-09-30
wildmanne39's apcmag will get your Windows installed but it is older and discusses grub (now called grub legacy) and all the new Ubuntus's use grub2.

After your install you can use this to reinstall grub2 to the MBR:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Or either of these:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by karrank% on 2011-10-05
Just finished, Success! (after a few hiccups, resolved by refering --rather, stumbling across, post #441--after having been directed by this most excellent forum--to the thread)

You folks rock, thanx.

side note--I've discovered that upgrading to 64-bit systems renders certain older yet perfectly functional hardware (printers and scanners in my case) obsolete. 

Hard lesson. Just learning it now.

---

### Post by wildmanne39 on 2011-10-05
Hi, I am glad you have ubuntu installed.
Enjoy

---

### Post by karrank% on 2011-10-05
> **wildmanne39 said:**
> Hi, I am glad you have ubuntu installed.
Enjoy

So are we. This box never had windows til now. A little headache-inducing really, only got it for a steep discount in an online sale and only for a couple of things(harmony remote s/w for one)

---

