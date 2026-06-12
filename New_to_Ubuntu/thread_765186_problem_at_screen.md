---
title: "problem at screen"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by winol5 on 2008-04-24
Hi, yesterday I intsalled ubuntu and it detected all right (also my reosluction) but not my graphic card, then it detected it but the resoluction changed to 1024x800 and I dont have the option to change it to 1280x1024 again, what Can i do?

---

### Post by swoll1980 on 2008-04-24
what kind of card?

---

### Post by prshah on 2008-04-24
> **winol5 said:**
> Hi, yesterday I intsalled ubuntu and it detected all right (also my reosluction) but not my graphic card, then it detected it but the resoluction changed to 1024x800 and I dont have the option to change it to 1280x1024 again, what Can i do?

Make a copy of your current xorg conf file```
cp /etc/X11/xorg.conf ~
``` then run the command ```
sudo dpkg-reconfigure xserver-xorg
``` which will (eventually) allow you to specify what resolutions you would like to use.

---

