---
title: "Server Authorization message on startup"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-07
i just finished doing a fresh install of ubuntu 8.10.  the install completed successfully, but when the OS begins to load after i have rebooted i get the following message on screen:

**Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user 105 and group 113.  Please correct the ownership or GDM configuration and restart GDM.**

does anyone have any idea what this message means and how i can correct this issue?

thanks.

---

### Post by Matt26 on 2008-11-07
i tried wiping the hard drive several times now (with Secure Wipe Pro and the manufacturer low level format utility) and i am still running into the same error- how can this be?

any help is appreciated.

---

### Post by Matt26 on 2008-11-12
i found the culprit here and it is a strange one- i have an 80GB western digital hard drive connected as an IDE slave drive (on the same channel as the boot drive).  once i disconnected it ubuntu came up fine.  anyone know what might cause this to happen?

---

### Post by goemonburo on 2009-01-03
I'm having what appears to be a similar issue but I'm getting (on boot...it runs through, seems to be loading Ubuntu fine...then blue screen and):

Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist.  Please correct GDM configuration and restart GDM.

I _did_ at one point have a flash drive plugged in (several days ago and I've used it fine up to now).  All I did between then and now is surf the web and play Sudoku. I'm leaving for a trip next week and am panicked if this computer (a Dell Mini 9, with 8.04) won't be usable.

Please help.  Thank you so much!

---

