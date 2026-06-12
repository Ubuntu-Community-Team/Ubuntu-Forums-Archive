---
title: "Formating Secondary Drives"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by diapaman on 2011-09-17
What's the best way to format a secondary hdd for cross-platform compatibility?

---

### Post by josephmills on 2011-09-17
> **diapaman said:**
> What's the best way to format a secondary hdd for cross-platform compatibility?

I cant say that it is the best way but might be easy to use gparted there is also other options but gparted is easy and works great google "format a secondary hdd gparted"

hope that this helps :)_

---

### Post by Lisiano on 2011-09-17
If you don't want to install any new software you can use try the Disk Utility under System -> Administration. A bit more user-friendly than Gparted, Gparted is more Poweruser-friendly.
Also you should use Fat32 as it is supported by everything (Windows, Linux, Mac OS, Mac OS X, Phones, everything). But if you wish to only target some devices like only Android phones and Linux you can use EXT. Do note that Windows can not see any partition AFTER the 1st one on a USB stick. (I have a bootable USB that I also use to move some files, Windows PC's can't mess with my USB but I can on Linux), not sure about USB HDDs.

---

### Post by sarwiz on 2011-09-17
> **Lisiano said:**
> If you don't want to install any new software you can use try the Disk Utility under System -> Administration. A bit more user-friendly than Gparted, Gparted is more Poweruser-friendly.
Also you should use Fat32 as it is supported by everything (Windows, Linux, Mac OS, Mac OS X, Phones, everything). But if you wish to only target some devices like only Android phones and Linux you can use EXT. Do note that Windows can not see any partition AFTER the 1st one on a USB stick. (I have a bootable USB that I also use to move some files, Windows PC's can't mess with my USB but I can on Linux), not sure about USB HDDs.
I really thank you for that info. I could use the second part of a usb drive to store personal info, etc, .  really great tip

---

### Post by Lisiano on 2011-09-17
If you want to hide some stuff from people you could try using TrueCrypt ([http://www.truecrypt.org/](http://www.truecrypt.org/)), quite a robust beast and works on all major platforms.

---

