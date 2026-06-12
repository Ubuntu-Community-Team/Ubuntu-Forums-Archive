---
title: "[SOLVED] Error Box for Synaptic"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by icyest on 2008-11-25
I received an error in this box:
[[IMG]http://img141.imageshack.us/img141/2293/screenshotsynapticlh2.th.png[/IMG]](http://img141.imageshack.us/my.php?image=screenshotsynapticlh2.png)[[IMG]http://img141.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
When opening Synaptic alone.

---

### Post by gn2 on 2008-11-25
Close Synaptic, open a terminal and run ```
sudo dpkg --configure -a
```

The error in your screenshot sometimes happens when an installation of packages, or an update is interrupted for some reason.

---

