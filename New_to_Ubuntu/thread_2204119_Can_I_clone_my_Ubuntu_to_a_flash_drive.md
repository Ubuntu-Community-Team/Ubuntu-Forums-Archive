---
title: "Can I clone my Ubuntu to a flash drive?"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by johnu1960 on 2014-02-06
Hi.  I have an Ubuntu 12.10 machine that is running well.  I would like to be able to create a bootable USB flash disk that contains the system.  (I don't have much data on the drive that contains the Ubuntu install.)  Is this possible?  Can anyone recommend a preferred software to do this?  I have heard of Ghost for Windows, perhaps there is something similar for Ubuntu?  

It would be great to be able to just restore from the USB drive in the event of a catastrophic crash.  I am really happy with the system exactly as it is now.  


Thanks in advance.

---

### Post by brokenhachi on 2014-02-06
Yes, but it would be highly impractical unless you're talking usb 3.0. You can use clonezilla maybe, or there is G4L (ghost for linux).

---

### Post by Vladlenin5000 on 2014-02-06
Clonezilla can do it perfectly (IF possible/advisable/practical... whatever).
I strongly suggest doing so with a normal HDD just in case.

---

### Post by PDA1 on 2014-02-11
Clonezilla can only do it IF what you're cloning is the same size or larger than the target.

Gparted would have to used to reduce the size of your System partition (if you have one) in the event that your System is too large to fit on the target.

Redo [http://redobackup.org/](http://redobackup.org/) is much, much easier to use.

Be warned- I've never been able to get Clonezilla or REDO to successfully reinstall the boot loader onto any image restore that I've done. But, it can be done easily enough from these directions- [http://crunchbang.org/forums/viewtopic.php?pid=361228](http://crunchbang.org/forums/viewtopic.php?pid=361228)

---

### Post by sudodus on 2014-02-11
You can make a tarball, which can be installed into the USB drive, if the total size of the files is small enough to squeeze into the USB drive (and allowing for some swap). Try the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by sudodus on 2014-02-11
But beware, the version 12.10 has only 18 months support. End of live will come soon (in April 2014). The next few versions have only 9 months support, but the coming version 'Trusty Tahr', 14.04, will get long time support (5 years, maybe less for some community flavour), similar to 12.04 LTS.

---

