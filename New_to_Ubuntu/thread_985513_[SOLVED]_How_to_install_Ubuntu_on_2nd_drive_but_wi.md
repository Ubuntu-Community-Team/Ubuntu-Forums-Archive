---
title: "[SOLVED] How to install Ubuntu on 2nd drive but with no dual boot option"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by tjsilver on 2008-11-17
Hi all,

I would like to install Ubuntu on an external USB HDD. However, I don't want the dual boot option. My BIOS lets me boot from a USB device and I would prefer to boot to Ubuntu that way.

Before anyone asks why, it's because my 'new' USB HDD is actually my old 3.5" IDE from my old desktop in an external enclosure - it's bulky.

Anyway, is it possible to install Ubuntu without it doing anything to my GRUB? If so, how?

Tim

---

### Post by caljohnsmith on 2008-11-17
All you need to do is click the "advanced" button at the final stage of the Ubuntu installation, and then set Grub to be installed to /dev/sdb or whichever is your external drive; just don't use (hd0) which is the internal drive. Then your USB drive will be bootable, and your internal drive will be untouched. :)

---

### Post by Crafty Kisses on 2008-11-17
You could technically unplug the internal HDD, then boot from the LiveCD with your external HDD plugged in, remember you don't have to do this, this is just a precaution, but select the external HDD, and install GRUB on the external HDD. I mean you're going to have to have install GRUB in order to boot Ubuntu to my knowledge. If you do not disconnect your HDD when you're installing make sure you select the advanced option in the installer and tell the installer to install GRUB to  **/dev/sdb** or whatever the external drive maybe called.

---

### Post by tjsilver on 2008-11-17
caljohnsmith and Codename,

Many thanks.

Tim

---

