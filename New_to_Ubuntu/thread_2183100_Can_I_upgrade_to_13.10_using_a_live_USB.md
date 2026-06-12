---
title: "Can I upgrade to 13.10 using a live USB?"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by AnnB on 2013-10-23
Hi!  I will be upgrading three PCs to Ubuntu 13.10 from 13.04 (a 32-bit and two 64-bit) and making two live USBs.  Can I make the 13.10 live USBs on my 13.04 installation and then upgrade the PCs from the USBs?  Hoping to skip some downloading...

Thank you!

---

### Post by grahammechanical on 2013-10-23
When you are running 13.04 try inserting the USB with 13.10 on it and you should get a dialog inviting you to upgrade to 13.10 from the USB stick.

Regards.

---

### Post by LotsOfQuestions on 2013-10-23
yes you can make a live usb down unetbootin from the software center and burn you 13.10 iso with that, it will delete everything so if you have items you want saved back them up or do a manual upgrade sudo apt-get intsall upgrade

---

### Post by Dennis N on 2013-10-23
You can make them all on your 13.04 system (both 32 and 64 bit), but they can only be used for doing new installations, if that is part of the question.

Edit: According to grahammechanical, you can now do upgrade instead of new install. Something I was unaware of.

---

### Post by Mark Phelps on 2013-10-23
Upgrading in-place can be a problematic situation -- as much can change between Ubuntu releases.  Unfortunately, there is no simple way to "roll back" to the prior version if anything goes wrong with the upgrade.  So, to be safe, you should use Clonezilla or RedoBackup to do an image backup of your current install.  That will allow you to restore the PC to a working version in only a few minutes.

---

### Post by AnnB on 2013-10-24
Thank you, everyone!  I've got two down and one to go - the 32-bit went OK (I got an error message and one missing package) and one of the 64s was perfect.  

Mark:  Thanks for the backup info.  I'm going to check these out before doing the last one - it has a separate partition for data files so a reinstall wouldn't be a catastrophe, but it's a newer PC with that UEFI Secure Boot and I had problems getting it to boot from the USB when I did the original 13.04 install - even after updating the boot info in the BIOS.  I think I ended up using BLoB.

---

