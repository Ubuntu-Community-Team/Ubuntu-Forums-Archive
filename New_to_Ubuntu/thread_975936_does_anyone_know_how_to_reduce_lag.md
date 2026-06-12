---
title: "does anyone know how to reduce lag?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by mikeftl on 2008-11-08
my computer is fast, but i am running ubuntu off a micro sd card which makes it very laggy at times.
Anyone know how to reduce lag?

---

### Post by earthpigg on 2008-11-08
preload?

```
sudo apt-get install preload
```

---

### Post by mikeftl on 2008-11-08
> **earthpigg said:**
> preload?

```
sudo apt-get install preload
```

whats taht do

---

### Post by ciscosurfer on 2008-11-08
> **mikeftl said:**
> whats taht do


Info taken verbatim from [http://packages.ubuntu.com/intrepid/misc/preload](http://packages.ubuntu.com/intrepid/misc/preload)
[INDENT]preload monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times. 

Note that installing preload will not make your system boot faster and that preload is a daemon that runs with root priviledges.[/INDENT]

---

