---
title: "[SOLVED] 2 Hard drives, one spare, Dual Booting Linux/Linux, Help needed."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by philinux on 2008-05-21
Already have ubuntu on one HD. Want to experiment with the other.

Problem is with second install it gets grub as well. And you end up with a grub on the both drives, but it's the second drive that's in command. Any kernel updates to first drive are then fubar. 

What I want is one grub on the first hard drive and not have it nobbled by the second install.

One solution here.

[http://www.linux.com/feature/113898](http://www.linux.com/feature/113898)

Anyone got other ideas.

---

### Post by bubba_169 on 2008-05-21
Not sure how you would do it exactly but you could try not installing grub at all for the second HD and make your own grub entry in /boot/grub/menu.lst on the first drive to boot from the second drive. You will need to install from the "alternate install cd" to get options on where to install grub.

Just a thought...

EDIT: Oops I should learn to read links first :oops:

---

### Post by philinux on 2008-05-21
Yes the live cd just ignores your original grub on the first hard drive.

---

### Post by philinux on 2008-05-21
Solved - alternate cd correctly identifies other system and offers to put grub on the first hard drive as I required. The live cd just hijacks your system and installs grub on the second hard drive.

Now i have duel boot 

sda1 ubuntu with grub on the mbr
sdb1 kubuntu with no grub.

---

