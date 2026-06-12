---
title: "Cannot boot, no CD nor USB"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by equitube on 2014-05-08
I am having similar issues. I have an old hp xh545 athlon iv. Cd drive doesn't work, bios doesn't support usb boot. I was finally able to reinstall wxp using plop boot mgr. 

I've been trying to install a linux distro for weeks from usb.  I tried many, none would install or even run live.

Yesterday I ran a mint 13 distro that I dont recall making. It ran live then I installed it. It found an installed distro of ubuntu (that never would boot). I chose the replace option and finished installation. 

Rebooting it, plop couldn't see the linux install and I could only run live off the usb. I found a similar issue on the mint forum. I ran a command to check the root partition , which seemed to be sdb6 (the mint seemed to be installed as a child to 'media' 

I also ran the partion utility to see the parts. I had a 10gb part with xp on it, a 7.75gb with linix, the mbr, 500mb part for linux swap.
I ran a command that was supposed to put grub in the mbr (I cant find the web page now in my history)

Upon reboot I'm at that minimal bash like screen of grub. I cant boot into anything, cant boot from usb, plop doesnt come up. No cd drive.

The floppy may work. Is there a command I can use to access anything? I don't know linux btw.

sorry for the length of this post, but I prefer to be complete rather than respond to dozens of shorter posts. Thank you for any help you can give

---

### Post by oldfred on 2014-05-08
Do you have a bootable floppy? 
My Red Hat install 15 years ago automatically make a recovery boot floppy drive.

If nothing boots about the only thing left is to remove hard drive an put it into another system. And use that system or its working CD or USB ports to make repairs.

How old is system and how broken is it?

---

