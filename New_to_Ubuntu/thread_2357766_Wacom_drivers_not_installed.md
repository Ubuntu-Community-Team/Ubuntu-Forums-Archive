---
title: "Wacom drivers not installed"
date: 2017-04-05
forum: New to Ubuntu
---

### Post by fmunizgeol on 2017-04-05
I've tried installing the package xf86-input-wacom-0.34.2 and failed with the following error:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found


I can't get those packages from sudo apt-get install. I'm new to Ubuntu. What should I do? I'm running Trisquel 7.0, actually, but I thought I could ask it here since it's based off Ubuntu. I installed it w/o the graphical interface installer, and when it asked me which software I wanted to install along, I chose only the desktop environment for Trisquel, terminal, and stuff like that, since I had no idea what the other ones do.

Thanks in advance.

---

### Post by tom167 on 2017-04-05
I'm kinda new to ubuntu too, but have you tried installing the missing packages?
Such as doing: ```
sudo apt-get install xorg-server xproto xext kbproto inputproto randrphoto
```

---

