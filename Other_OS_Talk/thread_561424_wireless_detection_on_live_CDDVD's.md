---
title: "wireless detection on live CD/DVD's"
date: 2007-09-27
forum: Other OS Talk
---

### Post by insane_alien on 2007-09-27
recently i've been trying out a number of distros. and i've noticed something odd. liveDVD's and live CD's do not detect my wireless interface. ubuntu still does it. nothing else.

for instance, i have a knoppix 3.something live CD it'll detect my wireless and log into the firt network(whether i want it to or not) but the latest live cd/dvd doesn't detect it. neither will the sabayon distro. and the gentoo one won't do it either(not sure if it is actually capable to be honest.)

has anyone else experienced this?

BTW it's an intel 2200 using the ipw2200 driver.

---

### Post by init1 on 2007-09-27
> **insane_alien said:**
> recently i've been trying out a number of distros. and i've noticed something odd. liveDVD's and live CD's do not detect my wireless interface. ubuntu still does it. nothing else.

for instance, i have a knoppix 3.something live CD it'll detect my wireless and log into the firt network(whether i want it to or not) but the latest live cd/dvd doesn't detect it. neither will the sabayon distro. and the gentoo one won't do it either(not sure if it is actually capable to be honest.)

has anyone else experienced this?

BTW it's an intel 2200 using the ipw2200 driver.
Experienced this? Yes, all the time. Mepis is the only distro that supports my wireless card without configuration. I need ndiswrapper for it to work.

---

### Post by insane_alien on 2007-09-27
yeah but what about previous versions working and the later versions not working.

---

### Post by init1 on 2007-09-27
> **insane_alien said:**
> yeah but what about previous versions working and the later versions not working.
Maybe it was an oversight. Or they tried to make it smaller by removing the drivers for some of the less common cards.

---

