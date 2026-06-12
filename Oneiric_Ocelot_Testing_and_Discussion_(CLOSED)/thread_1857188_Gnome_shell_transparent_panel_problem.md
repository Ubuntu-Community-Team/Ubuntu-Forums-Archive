---
title: "Gnome shell transparent panel problem"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by BigCityCat on 2011-10-09
I was trying this theme called nord and after installing I noticed there is a thin menu behind the panel that says FILE, EDIT, VIEW and so on. It looks like it has something to do with the global men. So I uninstalled appmenu but it's still there.

---

### Post by Spr0k3t on 2011-10-09
That's the global menu hiding behind there.  I believe there's a bug involved with it.  For now, I've removed it from my setup.

sudo apt-get remove --purge appmenu-gtk3

Of course I also removed all the other global menus as I don't like global menus... too much like mac.

sudo apt-get remove --purge appmenu-gtk appmenu-qt

Cheers!

---

### Post by BigCityCat on 2011-10-09
sweet thanks!

---

### Post by BigCityCat on 2011-10-09
hmmm It is telling me there is nothing to remove.

---

