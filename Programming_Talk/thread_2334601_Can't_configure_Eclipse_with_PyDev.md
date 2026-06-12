---
title: "Can't configure Eclipse with PyDev"
date: 2016-08-21
forum: Programming Talk
---

### Post by SteveZsuzska on 2016-08-21
I am running Lubuntu 16.04 and have installed Eclipse 3.8.1. I run eclipse from the command line, which allows me to install PyDev. However, when I go to Window -> Preferences PyDev does not appear on the list. If I try to reinstall PyDev it tells me that it is already installed. I think I have python installed because if I type python at the command line, I get a python interpreter. Any help would be appreciated.

---

### Post by Olav on 2016-08-21
From [http://www.pydev.org/download.html](http://www.pydev.org/download.html):
> PyDev does not appear after install!

Well, the main issue at this time is that PyDev requires Java 8 in order to run. So, if you don't want to support PyDev by going the LiClipse route (which is mostly a PyDev standalone plus some goodies), you may have to go through some loops to make sure that you're actually using Java 8 to run Eclipse/PyDev (as explained below).

Also, keep in mind that PyDev 5.x requires Eclipse 4.5 onwards (for Eclipse 3.8 use PyDev 4.x).
Eclipse 3.8.1 which is available in the Ubuntu repositories is old, I would prefer to manually install a more recent Eclipse (4.6). Then you would install Pydev through the update manager or Eclipse Marketplace.

---

### Post by SteveZsuzska on 2016-08-23
Many thanks Olav. I installed Neon Release (4.6.0) using the installer from the Eclipse website. I was then able to install and configure PyDev from within Eclipse.

---

### Post by Olav on 2016-08-24
Sounds good. By the way I do like PyDev myself.

---

