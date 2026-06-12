---
title: "cairo dock"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by davarse on 2008-07-25
hi... i've been running cairo dock for a while now. and i just apply auto hide and i set the position from the bottom screen edge bit too low and i can't get it come up again... 
does any one know how to fix it?? or just to bring up the configuration windows??
cheers i appreciate that a lot

---

### Post by Tim Sharitt on 2008-07-26
Hit Alt-F2 and enter:
```
killall cairo-dock
cairo-dock -m
```
That will bring up the maintenance screen on startup, which will allow you to change ant settings you need to.
If that doesn't work for some reason, the configuration file is ~/.cairo-dock/current_theme/cairo-dock.conf (on mine at least, should at least be somewhere in ~/.cairo-dock). You can edit your settings from there, or just set auto-hide=false so you can get to the configuration window (which is what I recommend unless you know exactly what your doing with the other settings).

---

