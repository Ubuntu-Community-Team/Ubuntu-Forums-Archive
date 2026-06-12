---
title: "Adding Ubuntu"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-03
Which package do I need to install for to add Ubuntu to my Kubuntu installation?

sudo apt-get install ....

---

### Post by Christmas on 2008-10-03
```
sudo apt-get install ubuntu-desktop
```
Used to be ubuntu-desktop-environment if I recall correctly (I'm on Debian so I can't verify).

---

### Post by halitech on 2008-10-03
are you looking for the full Ubuntu desktop or just the gnome desktop environment?

---

### Post by Konstabel on 2008-10-04
The full Ubuntu.

What would the code be just for the gnome environment?

---

### Post by halitech on 2008-10-04
if you want the full environment, do as Christmas posted. If you just want gnome, I believe its ```
sudo apt-get install gnome
```

---

### Post by Konstabel on 2008-10-05
What is the difference between installing only gnome and installing the full environment?

---

### Post by halitech on 2008-10-05
if you install gnome, you will only be able to run the gnome desktop using all the kde apps. If you install the full desktop, you will have both the kde apps and the gnome apps

---

