---
title: "ubuntu 14.04 launcher icons not displaying properly"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by johnsail on 2014-09-24
Following a recent upgrade the launcher icons are not displayed properly.

Changing the sixe of the icons does get them to display properly but when hovered over some display the icon name and with others it is unreadable,

Right click on each of them produces a box that cannot be read - but on some I am able to move into the unreadable box and display some of the options. Selecting an option generally produces the running progran EXCEPT with the software manager. When selected the whole screen becmes unreadable.

---

### Post by Vladlenin5000 on 2014-09-24
What Ubuntu version/flavor have you, first of all?
Have you previously installed themes and/or tweaked any desktop environment settings?

---

### Post by johnsail on 2014-09-24
Hi Galiza
Have used ubuntu/virtualbox for some time to make use of virtual machines. My ubuntu was supprted by a very able chap - but he has diappeared off the radar leaving me struggling.

How do I find out the version / flavour?

Not knowingly tweaked desktop environment settings except to change the size of the launcher icons so that the were readable.

John

---

### Post by Vladlenin5000 on 2014-09-26
So, whatever it is your version, you're sure you haven't changed the theme? 
Anyway, try the usual update:
```
sudo apt-get update
sudo apt-get upgrade
```

Then logout/login (or reboot).

---

### Post by johnsail on 2014-09-26
Seems that the problem caused by corrupt kernel.

Problem cleared as result of Slickymaster clearing my visualisation problem with virtualbox,

My thanks to Slickymaster

---

### Post by Vladlenin5000 on 2014-09-27
Please use the thread tools and mark it as solved.

---

