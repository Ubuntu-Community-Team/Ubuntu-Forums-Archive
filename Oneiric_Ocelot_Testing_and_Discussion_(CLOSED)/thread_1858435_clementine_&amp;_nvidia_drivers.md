---
title: "clementine &amp; nvidia drivers"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-10-12
If you are using clementine with the current 11.10 nvidia current drivers then it's likely that when exiting clementine 1 cpu will get pegged @ 100% or so.

If so & until there is an nvidia upgrade or some other fix it can be 'fixed' by  - 
```
gksudo gedit /usr/share/applications/clementine.desktop
```

Edit the Exec= line to look like this
```
Exec=env __GL_NO_DSO_FINALIZER=1 clementine
```

reference link
[http://code.google.com/p/clementine-player/issues/detail?id=2088](http://code.google.com/p/clementine-player/issues/detail?id=2088)

---

### Post by dino99 on 2011-10-12
hm, never had such issue (clementine-dev + nvidia 280 + pae kernel)

---

