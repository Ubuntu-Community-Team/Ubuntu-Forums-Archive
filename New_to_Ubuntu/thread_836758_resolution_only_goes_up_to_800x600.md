---
title: "resolution only goes up to 800x600"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by copper103 on 2008-06-21
my monitor is a neoview plug and play, capable of 1280x1024, but for some reason ubuntu is only letting me go up to 800x600, and i cant really use the computer efficiently at this resolution, please can someone help, my gfx card is an ati hd 2400 pro agpx8 which doesnt seem to be working

---

### Post by macaholic on 2008-06-21
Did you install the drivers from the restricted driver manager? (System > Administration > Hardware Drivers on gnome)

---

### Post by kwirk on 2008-06-21
Have you installed the ATI drivers for your graphics card?

You could try using envy to install if not.

sudo apt-get install envyng-gtk

Then run it from the applications --> System Tools... I think.

ADD: envyng is for Hardy Heron only, else use just envy

---

### Post by avtolle on 2008-06-21
Another suggestion on the monitor resolution problem if you are using 8.04. From the terminal (Applications>>Accessories>>Terminal)```
gksudo displayconfig-gtk
``` where you can look at both the monitor and the graphics card.

---

### Post by copper103 on 2008-06-21
ok thanks i fixed it

---

### Post by alienexplorers on 2008-06-21
Nice to hear you got it running!

---

