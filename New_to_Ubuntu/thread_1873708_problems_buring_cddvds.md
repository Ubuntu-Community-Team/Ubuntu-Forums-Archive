---
title: "problems buring cd/dvds"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by robalcorn on 2011-11-01
When using k3b discs burn extremely fast but also turn out unreadable using brasero i could leave on a jet and go on vacation and it will still be creating image for a simple dvd data project. If i reboot and go on other partition with opensuse and try everything is good to go any ideas??? could use the other partition for my media and not another o/s thanks to anyone who has a solution to this.

should also add i am running with gnome 3 not unity if that makes a difference

---

### Post by robert shearer on 2011-11-01
Try using xfburn....
```
sudo apt-get install xfburn
```

What are you trying to burn ??? Video/audio/data..?

---

### Post by robalcorn on 2011-11-03
Any data including yes videos, audio, pictures absolutely any data ...i have created a nice stack of coasters since i jumped from 11.04 to 11.10 ubuntu with a freash install.

---

### Post by robalcorn on 2011-11-03
Thanks xfburn works !!! (never heard of it before but nice program)

still confused as to why 11.10 using brasereo & k3b only makes unreadable discs but at least you gave me an alternative.

cheers :D

---

### Post by robert shearer on 2011-11-03
> still confused as to why 11.10 using brasereo & k3b only makes unreadable discs

Brasero has always been problematic for me whilst others find it operates faultlessly.
It is not my hardware as it happens on several machines and versions of Ubuntu. Unfortunately it is inconsistently inconsistent and sometimes works as it should !!

From the number of problems reported I fail to see why it remains the default burner when xfburn has matured to a more than competent replacement.

Happy it is working for you too.  :)

k3b **usually** works fine for me though I dislike all the dependencies involved when installing it, with what it drags in I may as well be running KDE as my desktop and be done with it. :)

---

