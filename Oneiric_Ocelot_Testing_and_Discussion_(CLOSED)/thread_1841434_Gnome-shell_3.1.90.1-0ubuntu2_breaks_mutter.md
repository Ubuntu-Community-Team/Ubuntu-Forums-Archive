---
title: "Gnome-shell 3.1.90.1-0ubuntu2 breaks mutter"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-09
The newest update of gnome-shell (3.1.90.1-0ubuntu2) does break mutter (3.1.90.1-0ubuntu1) at least with my 64-bit AMD setup, both from Oneiric repos.
The issue is that gnome-shell starts without panels.

I did workaround this by installing newer mutter and gnome-shell from Ricotz PPA.
Of course also gir1.2-accountsservice-1.0, gir1.2-caribou-1.0 and libcaribou0 must also be installed. Oneirics gnome-shell is built without those dependencies.

---

### Post by Harry33 on 2011-09-09
Also installing the missing dependency, gir1.2-accountsservice-1.0 did help.

---

