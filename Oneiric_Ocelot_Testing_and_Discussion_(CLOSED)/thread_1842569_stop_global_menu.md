---
title: "stop global menu?"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kornelix on 2011-09-11
I tried the old solution of removing the packages appmenu-gtk and appmenu-qt but this does not put the menus back on the application windows (at least not for nautilus and gedit). This is a show-stopper for me. Hope there is a way.

---

### Post by mc4man on 2011-09-11
> **kornelix said:**
> I tried the old solution of removing the packages **appmenu-gtk** and appmenu-qt but this does not put the menus back on the application windows (at least not for nautilus and gedit). This is a show-stopper for me. Hope there is a way.

It's appmenu-gtk3 that does the deed, or just
```
sudo apt-get purge appmenu*
```

---

### Post by kornelix on 2011-09-12
Many thinks, mc4man.

---

