---
title: "CCC-Compiling -- What do I miss?"
date: 2007-02-04
forum: Programming Talk
---

### Post by gummibaerchen on 2007-02-04
Hi,

I want to install the latest git version of CCC:
[http://live.gnome.org/Criawips/CriaCanvas](http://live.gnome.org/Criawips/CriaCanvas)

Check it out here:
git clone [http://www.blaubeermuffin.de/ccc.git](http://www.blaubeermuffin.de/ccc.git)

When I run "./autogen.sh" I get:
```
[FONT="Courier New"]Checking for required M4 macros...

  gtk-doc.m4 not found

Checking for forbidden M4 macros...

***Error***: some autoconf macros required to build libccc
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?[/FONT]
```


I need CCC in order to install Geom
([http://abulafia.fciencias.unam.mx/~canek/geom/](http://abulafia.fciencias.unam.mx/~canek/geom/))

Thanks!

---

### Post by Jussi Kukkonen on 2007-02-04
[http://packages.ubuntu.com](http://packages.ubuntu.com) says that gtk-doc.m4 can be found in the package *gtk-doc-tools*.

---

### Post by gummibaerchen on 2007-02-04
Thanks, problem solved.

---

