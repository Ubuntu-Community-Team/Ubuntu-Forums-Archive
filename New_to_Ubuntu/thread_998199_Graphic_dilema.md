---
title: "Graphic dilema"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-30
I've installed Ibex using a new card; Nvidia FX 5500 however the monitor settings seem fixed at 800x600 at 60Hz, -and when I install the recommended driver, it drops down to 600x480! There seem no way to get my 1600x1200 @ 75Hz unless i go back to my on board graphics!

And yet using openSuse on the same machine I have 1600x1200 @ 85Hz without installing a driver. Can I copy that driver or something?

---

### Post by SunnyRabbiera on 2008-11-30
this is one of the things ibex sucks at from what I have seen, it has horrid monitor detection and there is no easy fix for it anymore other then manually editing xorg.

---

### Post by nnjond on 2008-11-30
Thanks for your interest, Ive tried mamually editing, but im not sure what i'm doing. Have you any suggestions?

---

### Post by phidia on 2008-11-30
> **nnjond said:**
> Thanks for your interest, Ive tried mamually editing, but im not sure what i'm doing. Have you any suggestions?

You can't edit /etc/X11/xorg.conf anymore to change video card or monitor parameters because the configuration data isn't stored there now. 

It would be good to know where it is stored-it seems to be an Ubuntu secret-but perhaps it isn't very easy to edit in it's new location?

With the card you're trying to enable you could open synaptic and search for "nvidia" I believe you want the legacy card package also you want the nvidia-settings package. Install those and see if that works.

---

