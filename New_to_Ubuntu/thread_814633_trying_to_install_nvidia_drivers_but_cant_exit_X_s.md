---
title: "trying to install nvidia drivers but cant exit X server"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by mashamoo on 2008-05-31
Hey,

I am trying to install nvidia drivers, but I need to exit the X server first. I am doing a ctrl+alt+backspace to kill the current x server but it just restarts itself.

I then tried going ctrl+alt+F1 and killing the running x server (using kill -9) but it still restarts itself.

How do I exit the X server properly!?!?

HelP!

---

### Post by FuturePilot on 2008-05-31
I would really recommend installing the Nvidia drivers via Hardware Drivers. System&#8594;Administration&#8594;Hardware Drivers. Unless you need to manually install it for some reason, in which case run
```
sudo /etc/init.d/gdm stop
```
from a tty.

---

