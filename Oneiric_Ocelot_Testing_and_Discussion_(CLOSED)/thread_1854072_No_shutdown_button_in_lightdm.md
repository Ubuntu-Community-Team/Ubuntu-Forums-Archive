---
title: "No shutdown button in lightdm"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nordlicht.ol on 2011-10-03
Hi there,

while trying to get a relative clean gnome shell enviroment, I've purged a lot of packages (including unity and dependicies).

Now I don't have a shutdown button in lightdm. Does anyone know what packages are needed to get this back?

---

### Post by BwackNinja on 2011-10-03
Probably the indicator-* packages because that's where the shutdown buttons and such come from. Unity-greeter depends directly on libindicator.

---

### Post by crdlb on 2011-10-03
If you only want gnome, you may want to just use GDM.

---

