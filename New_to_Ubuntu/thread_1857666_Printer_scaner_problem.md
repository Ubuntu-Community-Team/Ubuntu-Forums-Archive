---
title: "Printer scaner problem"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by PGM12 on 2011-10-10
Hey guys. 
             I have managed to installed my brother MFC-8460N printer software and everything is fine with the printer but no matter what i have tried i can not get any of the 3 computers that are running 11.04 to even find the scanner. I did download the brother Linux software to no avail. Please help.

Thanks in advance

---

### Post by kurt18947 on 2011-10-10
The scanner *should* work in 11.04.  11.10 right now is a sorrier tale for me.  You do need to look at all the directions, both "before you install" and also the /lib/udev/rules.d/40-libsane.rules file edit if you're connecting via USB. Missing packages "CSH" or "TCSH" will cause scanner problems, as will missing sane-utils.  Good luck with it; the Brother scanners seem to work well once they're recognized.

---

