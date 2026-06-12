---
title: "If your only networking is wireless"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by walt.smith1960 on 2011-09-20
I'd recommend a little caution updating.  I just updated 11.10 and updates appear to have disabled my wireless networking.  I tried two different USB adapters. The adapters are recognized so I don't think it's a USB problem. One adapter is a RealTek and one is an Atheros 9K and neither one works.  I'll plug into an ethernet cable in a few hours and see how that works.  I wonder if occurrences like this are the reason for for not using Beta software when reliability matters :tongue:.

---

### Post by castrojo on 2011-09-20
See the sticky, it's a problem with ca-certificates removing an nss library.

---

### Post by walt.smith1960 on 2011-09-21
Fixed.  It may well have been something to do with ca-certificates.  I saw the other thread and checked for the named file. It was there but I downloaded and reinstalled anyway. I then shut down, restarted and no luck. I then shut down, plugged into a wired internet connection and the wireless adapter immediately came to life.  I ran update/upgrade and among the updates was something about ca-certificates.  I then shut down, unplugged the wired network connection, restarted and wireless works.  Heh :D

---

