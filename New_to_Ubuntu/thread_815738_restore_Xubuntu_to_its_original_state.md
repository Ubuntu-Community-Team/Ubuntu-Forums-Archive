---
title: "restore Xubuntu to its original state"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by xecure on 2008-06-01
I installed Xubuntu today and enabled compiz shortly afterwards, ever since then my GUI is not working properly, the windows are 'stuck' to the top left of the screen and the menu is hidden. Is it possible for me to run a code in terminal that will restore Xubuntu to its complete original form? (remove files and software installed and all)

---

### Post by spiderbatdad on 2008-06-01
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` This should restore your original video settings. Remove unwanted packages via synaptic package manager. There is no restore to original state command, but you can remove unwanted packages via synaptic or aptitude.

---

### Post by linux phreak on 2008-06-02
Press alt+F2.In that type  xfwm4 --replace.

---

### Post by Paqman on 2008-06-02
For what it's worth, XFCE actually includes a compositing window manager by default. It can't do all the flashy stuff Compiz can like wobbly windows and cubes, but it will do dropshadows and transparency. It'll also allow you to use things that require a compositor, like Avant Window Navigator.

So even without Compiz you can have some nice desktop features.

---

