---
title: "[SOLVED] Boot only to text mode since installation of graphics card"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Felixworks on 2008-11-20
I have Ubuntu installed on a Dell from 2004-ish.  It's graphics were powered by some crappy Intel integrated chip so I put in an nvidia geforce mx 440 I had laying around.  Now when I boot up, instead of getting the normal graphical interface, it's all text.  How do I get back to the normal graphics?  Is this just a simple fix or does it indicate that the graphics card is bad?

---

### Post by taurus on 2008-11-20
See if you can reconfigure your X server for the new nVidia card.  After log in, try

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm
```

---

### Post by Felixworks on 2008-11-20
Wow thanks that worked right away.

---

