---
title: "error: QtGui/QApplication: No such file or directory"
date: 2013-10-14
forum: Programming Talk
---

### Post by MikeCyber on 2013-10-14
Hi
it worked on 12.04 but in 13.04 i get:
main.cpp:3: error: QtGui/QApplication: No such file or directory

What am I missing? Many thanks

---

### Post by spjackson on 2013-10-14
Are you trying to use Qt 4 or 5?
Are you trying to use a repository development package for the libqt library or have you installed it via another means?
How are you trying to build e.g. qmake+make or QtCreator or what?

---

### Post by MikeCyber on 2013-10-14
setting default to qt4 did help.

---

