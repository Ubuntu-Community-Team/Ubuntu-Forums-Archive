---
title: "Unity 3d/Gnome3 desktop flicker"
date: 2011-05-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-05-30
Hi guys,

I am running oneiric in a vm with 1.3 gigs of memory allocated.  Whenever i change the session to gnome3 or unity 3d and log in, the shell continuously flashes, making it unusable. Anyone else have this problem?

---

### Post by Quadunit404 on 2011-05-31
Well, what virtualization platform are you using? The only virtualization platform Unity and GNOME Shell work reliably in is VirtualBox, and even then you need to install guest additions and enable 3D acceleration.

---

### Post by Squonk07 on 2011-06-02
I'm having the same problem, though only when I try to log into GS. In fact it's worse because, after a minute, GS crashes and forces me to log out. Unity works fine. I'm similarly testing in a VM (VirtualBox) and have installed Guest Additions and have enabled 3D acceleration. In fact, I have three OO machines--two upgraded from a Natty install and a third made from a fresh download of OO alpha 1. The latter is the one that's giving me the trouble--the other two will log into a GS session but have problems of their own (unusably slow screen redrawing).

---

