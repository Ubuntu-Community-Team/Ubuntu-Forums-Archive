---
title: "stuck in low graphics mode, can't find soundcard!"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by maloko1 on 2008-07-30
My desktop is booting straight into low graphics mode, The resolution won't go past 800x600 without my screen going into pylons. I've tried installing envy which doesnt appear is my system tools, I use an ATI SB400 graphics card i think and i can't think of what to do to fix this as i'm new to Ubuntu. Also for some reason my sound card isn't being detected at all, along with it telling me " No volume control GStreamer plugins and/or devices found. What to do? :(

---

### Post by gvartser on 2008-07-30
check out:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

/g

---

### Post by northern lights on 2008-07-30
As for the graphics, run ```
sudo /etc/init.d/gdm stop
```to temporarily exit the graphical desktop environment (jot down next two lines in advance). Then reconfigure X```
sudo dpkg-reconfigure -phigh xserver-xorg
```restart the desktop environment```
sudo /etc/init.d/gdm start
```

Check under "System > Administration > Hardware Drivers" whether there's a proprietary driver to activate for your card.

For the sound issues, can you post the output of ```
cat /proc/asound/cards
```Thank you.

---

