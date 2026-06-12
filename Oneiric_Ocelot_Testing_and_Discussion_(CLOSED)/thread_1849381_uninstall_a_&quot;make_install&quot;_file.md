---
title: "uninstall a &quot;make install&quot; file"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rootnet47 on 2011-09-24
[SIZE=2]Hi! I'm new to Linux and I'm using Ubuntu 11.10 Oneiric Ocelot  beta 1. Well, I've Installed 
[/SIZE][SIZE=2]libgraph-1.0.1[/SIZE][SIZE=2].tar.gz package to run c graphics programs, but at the time of installation on I put the extract file on my desktop and made it install. But after that I've removed the [SIZE=2]extract  the file by "rm -f -r"[/SIZE][/SIZE][SIZE=2]. Well, my doubt is that 
Does the[/SIZE] [SIZE=2]libgraph-1.0.1 package works farther where I removed the extracted DIR?
[/SIZE]

---

### Post by Elfy on 2011-09-24
Thread moved to Ubuntu +1 (Oneiric Ocelot). Please used Development forums for dev versions

---

### Post by cariboo on 2011-09-24
Once the program/library has been compiled and installed, you don't need the source directory anymore, except if you want to uninstall the program/library, by running:

```
make uninstall
```

---

### Post by mc4man on 2011-09-24
If you did a default configure & a **sudo **make install then a number of files would have been installed to /usr/local/*

If your intention is now to uninstall/remove then you could manually search out & delete, some may be obvious, others not
(depending on whether you've installed other sources to /usr/local

The easiest way would be to extract the source again, configure/make/make install exactly as before, then run a
sudo make uninstall

(if in fact you did a sudo make install and deleted the source/build dir.

---

