---
title: "problem with hotspot connection"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by mehoody on 2012-09-28
hi everyone
i recently installed lubuntu 12.04 on my netbook and when i try to connect to a hotspot he asks me for authentification.
before installation i tried it (without installing) and it worked fine.
does anyine have any idea?

---

### Post by theinfinitestrike on 2012-09-28
Is it possible that the hotspot provider has changed the settings and now requires authentication? If you are in a public place, like a coffee shop, sometimes they may require that someone buy something before they allow access to the web.  

If you are concerned about it being a hardware issue you might try to input  this into a terminal

```
dmesg | tail
``` Or use the "log file viewer", which is probably under your "System" menu  to see if your kernel log files offer any indication of some sort of problem.  hope these ideas help

---

