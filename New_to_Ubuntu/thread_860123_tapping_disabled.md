---
title: "tapping disabled"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-15
I have a Toshiba A215-S5837 notebook running ubuntu 8.04.1, I was able to disable touchpad tapping by making the following change to /etc/X11/xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
...
[COLOR="Red"]Option "MaxTapTime" "0"[/COLOR]
...
EndSection

---

### Post by bobnutfield on 2008-07-15
Thanks for that.  Many will find it useful.  You can also install a GUI to adjust tapping called GSynaptics.

Bob

---

