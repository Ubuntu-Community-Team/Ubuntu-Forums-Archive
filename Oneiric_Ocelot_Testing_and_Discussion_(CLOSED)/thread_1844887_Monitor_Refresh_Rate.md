---
title: "Monitor Refresh Rate?"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teejay17 on 2011-09-15
How can I change the monitor refresh rate in Ubuntu 11.10? I see I can change the resolution under "Displays," and I can rotate a full 360 degrees, but there's no option to change the refresh rate...

---

### Post by dino99 on 2011-09-16
only CRT needs (sometimes) refresh rates into xorg.conf, otherwise lets the kernel doing its job smootly, no need to disturb it

---

### Post by anders_c_ on 2011-09-17
you can change rate with "xrandr" in a terminal.
just typing xrandr will give you a list of available resolutions.

xrandr -s WIDTHxHEIGHT -r RATE

---

### Post by teejay17 on 2011-09-17
> **anders_c_ said:**
> you can change rate with "xrandr" in a terminal.
just typing xrandr will give you a list of available resolutions.

xrandr -s WIDTHxHEIGHT -r RATE

That is helpful. Thanks.

---

