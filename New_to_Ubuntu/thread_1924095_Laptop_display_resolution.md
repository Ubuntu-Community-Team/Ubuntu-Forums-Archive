---
title: "Laptop display resolution"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by redsoxfan45 on 2012-02-12
Hey! I can't get my display to allow me to choose a resolution higher the 1024 x 768.  ATI radeon x300 integrated card.  Any thoughts?
Ubuntu 11.10

---

### Post by Rodney9 on 2012-02-12
Today's X rarely requires manual configuration. X now automatically configures itself with reasonable defaults. Both GNOME and KDE provide GUI utilities for customizing settings beyond these defaults if you like.

However, sometimes you need to muck with the configuration manually, beyond what these tools allow. 
Read more on configuring xorg here -

[https://wiki.ubuntu.com/X/Config/](https://wiki.ubuntu.com/X/Config/)

Rodney

---

### Post by Mark Phelps on 2012-02-12
It's likely you won't be able to do what you want  The ATI restricted drivers offered higher resolutions -- but ATI dropped Linux driver support for your card years ago.  So now, you're stuck using the default open-source AMD driver -- and it may not support enhanced resolutions.

---

