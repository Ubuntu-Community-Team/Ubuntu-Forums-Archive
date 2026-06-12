---
title: "Replace LightDM with GDM?"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2011-09-25
Is it possible to replace LightDM with GDM. LightDM does not well for multiple user accounts. I tried
```
sudo dpkg-reconfigure lightdm
``` selecting GDM but GDM does not start.

---

### Post by MacUntu on 2011-09-25
Are you sure it doesn't start? Maybe it just crashes (that is what it did here a few weeks ago) - have a look at '/var/crash' if you see any gdm related crash.

---

### Post by foxy123 on 2011-09-25
> **MacUntu said:**
> Are you sure it doesn't start? Maybe it just crashes (that is what it did here a few weeks ago) - have a look at '/var/crash' if you see any gdm related crash.

No, there is nothing there related to GDM.

---

### Post by tista on 2011-09-25
Guys,

...umm ...sounds strange. :sad:
I'm running gdm 3.0.4-0ubuntu11 instead of lightdm.
See my pstree:
[http://paste.ubuntu.com/696646/]("http://paste.ubuntu.com/696646/")

cheers.

---

