---
title: "cannot install libgda-3.0.0"
date: 2014-09-04
forum: Programming Talk
---

### Post by kevin_ on 2014-09-04
i'm trying to install libgda-3.0.0 which is required to install libgnomedbmm
when runs ```
./configure
```  got this : [https://gist.github.com/anonymous/e4e3f2c3703c29e8e5c1](https://gist.github.com/anonymous/e4e3f2c3703c29e8e5c1)

when runs ```
make
``` got this : [https://gist.github.com/anonymous/de53e0f90e4eaf0d3a26](https://gist.github.com/anonymous/de53e0f90e4eaf0d3a26)

greatly *appreciate any help* you can give me

---

### Post by spjackson on 2014-09-04
Welcome to the forums.

What are you ultimately trying to achieve? The error message during make suggests to me that libgda-3 is not compatible with glib2. I would recommend installing as many recent prerequiste libraries via a package manager, rather than building old versions from source, unless you have a real need to do that.

---

### Post by kevin_ on 2014-09-10
i just want to install **libgnomedbmm** it asks for **libgda-3.0.0**

---

### Post by spjackson on 2014-09-11
But why do you want to install libgnomedbmm? It appears to be old and not maintained. It was available in Ubuntu until being dropped in karmic (2009) because of its dependence on GTK 1.2. See [https://launchpad.net/ubuntu/+source/gtkmm/+changelog](https://launchpad.net/ubuntu/+source/gtkmm/+changelog)

In my opinion, your best chance of installing libgnomedbmm is to install a sufficiently old Linux (e.g. Ubuntu jaunty or earlier) that provides the old dependencies. To get it to work on a recent Ubuntu would require porting it, as far as I can tell.

---

