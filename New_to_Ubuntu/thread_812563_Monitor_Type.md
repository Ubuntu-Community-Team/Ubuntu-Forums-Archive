---
title: "Monitor Type"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by jeremymiles on 2008-05-30
Since installing Ubuntu (Hardy), I've changed my monitor.  When I did the installation, at some point there was a long list where I could set my monitor type.  I'd like to get back to that, so I could get the refresh rates correct, but I can't find it.

Does anyone know where it is?

Thanks,

Jeremy

---

### Post by warbread on 2008-05-30
```
:-$ sudo dpkg-reconfigure xserver-xorg
```

If you are attached to your /etc/X11/xorg.conf file, back that up first.  This will over-write it.

---

