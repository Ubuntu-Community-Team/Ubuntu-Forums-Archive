---
title: "Compiz consuming a LOT of ram"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gunss on 2011-08-20
Right now with a fully updated system compiz is consuming 343.1 of RAM and upping every ~10 seconds.

Only firefox and htop is open.

---

### Post by MacUntu on 2011-08-21
Compiz, Unity, the indicators - everything is leaking like hell right now. In its current state I cannot run Ubuntu longer than a week before I have to reboot. :-(

Fortunately Launchpad is full of bug reports about it, so some of those problems likely will get fixed over the next few weeks.

---

### Post by mc4man on 2011-08-21
Seems to have gotten even worse just this week
On 2 installs w/ todays daily the mem use just at login itself has increased
W/ nvidia 450MB+ on 64 bit, 250MB on 32bit
(and this is with some unneeded disabled

compiz is up almost 10+% from  08/15 installs, slightly more on 64 bit

What's surprising here is aptd is always running, don't believe I've seen that before, or if it was it was a very small user
On 64 bit w/ nvidia using 92MB, recorded a few min. after login
On 32 bit w/ nvidia 44MB,  13MB w/ nouveau, 

Edit - on the 32 bit install aptd only runs for a few min, on the 64 it never closed

---

### Post by ventrical on 2011-08-21
On my fresh install (last night) it starts at 38.0 and slowly starts to crawl up.

 I'll check my back-step version.

current  3.0.0-8

---

### Post by dino99 on 2011-08-21
purging then reinstalling is often an easy way (compiz and the like)

---

### Post by ftx79 on 2011-08-21
> **ventrical said:**
> On my fresh install (last night) it starts at 38.0 and slowly starts to crawl up.

 I'll check my back-step version.

current  3.0.0-8

Try a "static" wallpaper. That works for me...

---

### Post by Gunss on 2011-08-21
> **MacUntu said:**
> Compiz, Unity, the indicators - everything is leaking like hell right now. In its current state I cannot run Ubuntu longer than a week before I have to reboot. :-(

Fortunately Launchpad is full of bug reports about it, so some of those problems likely will get fixed over the next few weeks.


I'm using a 32bit system and the system was only on for 3 hours.

I'm using vanilla kernel 3.0.1. It works better than ubuntu kernel for now.


ps: the same bug happens with ubuntu kernel too.

---

### Post by jerrylamos on 2011-08-21
Yeah, Compiz consumes a lot, especially space in "Launchpad Bugs".

Only reason I run it is to find more bugs in a new ubuntu  release.

Compiz locks up xorg on my fastest pc which has ati radeon xpress 200.

Of course, since the pc is locked up, can't run anything including ubuntu-bug xorg.

When I want to get something done on that pc I run Unity-2D or else Narwhal or Meerkat or Lynx.  Certainly not Oneiric Unity-3D.

Jerry

---

