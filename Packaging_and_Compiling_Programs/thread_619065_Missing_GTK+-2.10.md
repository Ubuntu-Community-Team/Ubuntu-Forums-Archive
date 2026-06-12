---
title: "Missing GTK+-2.10"
date: 2007-11-21
forum: Packaging and Compiling Programs
---

### Post by King_Critter on 2007-11-21
I'm trying to compile the Aurora GTK Engine. But whenever I run ./configure, it gives me this error: ```
configure: error: GTK+-2.10 is required to compile aurora
``` I looked in Synaptic for any packages with GTK in their names, but the closest I could find was other GTK engines. So what do I need?

---

### Post by dholbach on 2007-11-21
```
sudo apt-get install libgtk2.0-dev
```

We are >= 2.10 since Edgy.

---

### Post by King_Critter on 2007-11-21
Awesome, works perfect! Thanks.

---

### Post by matigol on 2009-03-16
Perfect !

Thx.

---

### Post by Phayder92889 on 2009-05-10
Awesome! thanks!

---

