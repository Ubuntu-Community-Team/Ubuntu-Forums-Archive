---
title: "[SOLVED] Need permission to modify xorg.conf file."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Trapezium on 2008-08-31
Excuse the general noobery of this question (hey, this is what the forum's for, right?), but I need to modify the etc/X11/xorg.conf file and I don't have the permission. How on earth do I do it?

---

### Post by cdtech on 2008-08-31
Open a terminal and type:
sudo gedit /etc/X11/xorg.conf

---

### Post by Trapezium on 2008-08-31
You're a legend. Thanks. :)

---

### Post by ajgreeny on 2008-08-31
However, one could ask why you need to edit that file and in what way do you need to change it?  There could be other ways to get to where you need to without a manual edit, and if you get it wrong you could end up with only a console screen, no GUI.

---

