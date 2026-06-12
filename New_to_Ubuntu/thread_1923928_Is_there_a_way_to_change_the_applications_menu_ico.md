---
title: "Is there a way to change the applications menu icon?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2012-02-11
[Ubuntu 10.04]

That's it, really. I can change the icons in the menus themselves, but not the icon for the menu itself (like you can do in KDE)

---

### Post by doppel.ganger on 2012-02-11
Try replacing this picture with one of your choice: /usr/share/icons/gnome/24x24/places/start-here.png
Then run:
```
gtk-update-icon-cache /usr/share/icons/gnome
```
Then try logging out and back in.

---

### Post by AlvitrValkyrie on 2012-02-11
That did not seem to do the trick :l

---

### Post by doppel.ganger on 2012-02-11
What version of gnome are you using?

---

### Post by AlvitrValkyrie on 2012-02-11
Gtk 2

---

