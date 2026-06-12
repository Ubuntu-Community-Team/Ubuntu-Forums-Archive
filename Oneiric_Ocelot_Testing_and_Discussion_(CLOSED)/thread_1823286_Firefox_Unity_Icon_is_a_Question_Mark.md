---
title: "Firefox Unity Icon is a Question Mark"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Anthony M on 2011-08-11
Ever since the upgrade from 11.04 to 11.10 by Unity Firefox icon is a question mark.

Any idea how to fix/change this?  Are Unity icons customizable?

Thanks!

---

### Post by Johnb0y on 2011-08-11
tried just removing and re-adding it?

---

### Post by Anthony M on 2011-08-12
> **Johnb0y said:**
> tried just removing and re-adding it?

Yep, tried it ;) Doesnt work

---

### Post by Sam White on 2011-08-12
Tried completely reinstalling FF? Or is that what you meant?

---

### Post by Anthony M on 2011-08-12
> **Sam White said:**
> Tried completely reinstalling FF? Or is that what you meant?

I've tried removing the icon from Unity then re-adding it and it stays the same. If I reinstall FF will I loose my bookmarks, profile and such?

Thanks!

---

### Post by lucazade on 2011-08-12
> **Anthony M said:**
> I've tried removing the icon from Unity then re-adding it and it stays the same. If I reinstall FF will I loose my bookmarks, profile and such?

Thanks!

no, you won't loose settings, they are stored in /home/username/.mozilla/..  and will remain even if you uninstall firefox.

you can try to update iconcache, maybe it is broken.. try with:
```
sudo gtk-update-icon-cache /usr/share/icons/Humanity
```

---

### Post by Anthony M on 2011-08-12
Unfortunately, none of these suggestions have worked.  I noticed the icon for "Browse the Web" in the dashboard is blank as well....

Is gnome-tweak capable of changing Unity icon settings?

---

### Post by Johnb0y on 2011-08-12
> **Anthony M said:**
>  If I reinstall FF will I loose my bookmarks, profile and such?

technically nope, but you can export your book marks etc and re-add them later... :D

---

