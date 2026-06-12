---
title: "How to stop X?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by itsStephen on 2008-11-26
I'm trying to install the nvidia driver myself because the only one in the driver thing is an old one.

So how do I stop X? I've read a few things but they don't work (probably because they're years old).

---

### Post by OutOfReach on 2008-11-26
To kill X, press Ctrl+Alt+Backspace.

---

### Post by inobe on 2008-11-26
what version if it ?

---

### Post by itsStephen on 2008-11-26
Thanks

This driver doesn't have that annoying bug where it covers icons with a blue square!

---

### Post by SuperSonic4 on 2008-11-26
ctrl+alt+backspace will reset X not kill it.

Press ctrl+alt+F1 to drop to a command prompt and install from there

you should always back up xorg before doing anything though

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

