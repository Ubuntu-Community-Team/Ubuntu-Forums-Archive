---
title: "PCF Font Install"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-05-12
I am needing to install the snap font by artwiz, and when i followed the directions in this guide: [http://www.ubuntugeek.com/howto-install-artwiz-fonts-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-artwiz-fonts-in-ubuntu.html), and i select the font it shows up as nothing but blocks.  All i have done besides this guide is placed the font in the fonts folder.

---

### Post by Mauler5858 on 2008-05-13
bump

---

### Post by Mauler5858 on 2008-05-13
Hopefully somebody knows about this.....bump

---

### Post by smudi on 2009-04-25
[http://ubuntuforums.org/showthread.php?p=7143817](http://ubuntuforums.org/showthread.php?p=7143817)

---

### Post by tocki on 2009-11-12
I had the exact problem like you did and finally found out that all you have to do is delete the following file


$ sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf


then run


$ sudo fc-cache -f -v


now your bitmap fonts will be recognized.

---

