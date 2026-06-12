---
title: "Indicator-applet in gnome3-fallback"
date: 2011-06-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by espenfjo on 2011-06-10
Hi,
Are there any information about the indicator-applet in gnome3-fallback?

---

### Post by jbicha on 2011-06-10
The status menus (indicators) have not been ported to GTK3 yet. When they are, then you'll be able to use them in the fallback session, but I think you will have to add them to the panel yourself to replace the clock, network applet etc. (just choose the indicator session from the Add to Panel selector). Since Gnome Shell & the fallback sessions are not shipped by default, I believe the desire is for those sessions to be closer to upstream to make maintenance easier and presumably that's what the "Gubuntu" folks are wanting anyway.

---

### Post by AllRadioisDead on 2011-08-25
Any word on this? Should be possible now that Unity is based on GTK3.

---

### Post by jbicha on 2011-08-25
It just needs some developer to port it over but most of the developers are busy trying to get the rest of Ubuntu ready for beta, and then release. I, for one, don't have the C coding skills necessary.

 [https://bugs.launchpad.net/indicator-applet/+bug/724369](https://bugs.launchpad.net/indicator-applet/+bug/724369)

---

### Post by lucazade on 2011-08-25
unfortunately no.
nobody is porting indicators in fallback session.

---

### Post by AllRadioisDead on 2011-08-25
There's hope!

[QUOTE="Dmitry Shachnev (mitya57) "]I want to do this, but I'm on holidays now and the only Internet
connection here is my phone, so most probably I won't be able to do
this until September. Even if it will be too late, I can use a PPA.

See full activity log
[/QUOTE]

---

