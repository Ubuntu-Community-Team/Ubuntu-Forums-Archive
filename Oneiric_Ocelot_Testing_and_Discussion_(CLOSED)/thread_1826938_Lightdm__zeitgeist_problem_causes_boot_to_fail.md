---
title: "Lightdm / zeitgeist problem causes boot to fail"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by frup on 2011-08-17
The latest set of updates causes lightdm to freeze and fail to load.

I dropped in to tty and started lightdm under sudo.

The screen returns to where boot has failed.

returning to tty shows:

lightdm symbol lookup error: /user/lib/gio/modules/libgiozeitgeist.so undefined symbol: g_desktop_app_info_launch_handler_get_type

---

### Post by dino99 on 2011-08-17
should be fixed by latest package from "main" server now

---

### Post by frup on 2011-08-17
Ta, should have thought of that myself.

---

### Post by rbrick49 on 2011-08-17
> **dino99 said:**
> should be fixed by latest package from "main" server nowI just updated from main server Dino file was there to fix unity but mine is more corrupt than it was before also gnome-shell is acting weird also

---

### Post by dino99 on 2011-08-17
hey some patience needed there ;) gs like some other packages are waiting to be ported to 3.1.5, might be done till next week.

---

### Post by Harry33 on 2011-08-17
See that you have updated to this glib2.0 package:
glib2.0 (2.29.16-0ubuntu2)

That will remove the troublesome libzeitgeist-gio.
You can also remove it manually.

---

### Post by rbrick49 on 2011-08-17
> **Harry33 said:**
> See that you have updated to this glib2.0 package:
glib2.0 (2.29.16-0ubuntu2)

That will remove the troublesome libzeitgeist-gio.
You can also remove it manually.yes its all ok again Harry thank you I was jumping the gun a bit I think like Dino said patience
regards ron

---

