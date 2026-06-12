---
title: "Can't compile Jabbin 2.0 BETA"
date: 2006-08-01
forum: Packaging and Compiling Programs
---

### Post by X.Cyclop on 2006-08-01
The INSTALL file says that you need to type this for compiling Jabbin:
```
  
  $ qmake jabbin.pro
  $ make
```
But, when i type the first line i get an error: **sudo: qmake: command not found**.

I've installed **libqcad0**, **libqt3-mt** and **zlib1g** and it doesn't work.

What can i do?:confused:

---

### Post by mlind on 2006-08-01
qmake is provided by **qt3-dev-tools** package. Try installing that first.

---

### Post by X.Cyclop on 2006-08-01
It works.:D 

Thanks a lot!;)

---

### Post by www.rzr.online.fr on 2008-06-27
FYI, I packaged latest snapshot version , test feedback welcome :

[http://rzr.online.fr/q/jingle](http://rzr.online.fr/q/jingle)

---

