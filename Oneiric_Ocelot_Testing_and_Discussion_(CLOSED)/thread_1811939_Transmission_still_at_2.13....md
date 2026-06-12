---
title: "Transmission still at 2.13..."
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JerecDrak2 on 2011-07-25
Hey everyone,

I noticed that the version of Transmission in the Oneiric archive is lagging behind at 2.13, while 2.33 was released recently. Does anyone know if there are plans to update the package in the archive? Or how to request this?

Change list is [here]("https://trac.transmissionbt.com/wiki/Changes#version-2.33") for those interested :KS

---

### Post by Harry33 on 2011-07-25
The version 2.32 has been uploaded into Launchpad 2011-7-19 already.
But there is a dependency wait for the package libnatpmp-dev.

> Build status
 Dependency wait on allspice (amd64)

Missing build dependencies: libnatpmp-dev
Started on 2011-07-19
Finished on 2011-07-19 (took 12.5 seconds)
buildlog (1.5 KiB)

---

### Post by jbicha on 2011-07-25
Right, like Harry33 says, Transmission 2.32 or 2.33 is waiting on several [Main Inclusion Requests]("https://wiki.ubuntu.com/MainInclusionProcess").

[http://pad.lv/813308](http://pad.lv/813308) [http://pad.lv/813313](http://pad.lv/813313) [http://pad.lv/813318](http://pad.lv/813318)

Those should be approved soon. There is no need to request action, since it's already being worked on. :-)

---

### Post by JerecDrak2 on 2011-07-26
That's great news, thanks for the replies guys :D

---

