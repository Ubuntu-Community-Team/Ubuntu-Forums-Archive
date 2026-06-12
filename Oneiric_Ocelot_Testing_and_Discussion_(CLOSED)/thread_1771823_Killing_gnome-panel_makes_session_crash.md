---
title: "Killing gnome-panel makes session crash"
date: 2011-05-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-05-30
If I kill gnome-panel suddenly the current session crashes with a nice dialog and I've to login again.

pkill gnome-panel or killall gnome-panel.. after killing a second time there is a crash.

Is this intended to be, like an error detection, or a bug? Any way to avoid this behavior?

I'll try to launch session in debug mode to figure out what's wrong.



it is probably this... 
gnome-session[10698]: WARNING: App 'gnome-panel.desktop' respawning too quickly

---

### Post by MacUntu on 2011-05-30
Don't know, but got that "Oh no! Something has gone wrong." dialog too.

---

