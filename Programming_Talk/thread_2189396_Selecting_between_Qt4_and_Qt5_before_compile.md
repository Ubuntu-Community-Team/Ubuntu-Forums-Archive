---
title: "Selecting between Qt4 and Qt5 before compile"
date: 2013-11-22
forum: Programming Talk
---

### Post by dargaud2 on 2013-11-22
Hello all,
Currently in my ubuntu setup, if I want to compile a project with Qt5, I simply run ```
qmake && make
```. And if I want to compile with Qt4, I can do ```
/usr/share/qt4/bin/qmake && make
```
 

But I have a large project where the qmake sequences are shrouded in  scripts. It runs only with Qt4 but running the scripts directly uses the  default, which is Qt5, so the compilation fails. Is there an environment variable (or some other  method) I can set to tell the script to use Qt4 by default ? Is that what qtchooser is for ?

---

### Post by dargaud2 on 2013-11-22
OK, I've found a way:
```
QT_SELECT=qt4 QTDIR=/usr/share/qt4 PATH=/usr/lib/x86_64-linux-gnu/qt4/bin:/usr/bin:/home/dargaud/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin qmake && make
``` and for qtcreator, delete the .pro.user file and launch ```
QT_SELECT=qt4 QTDIR=/usr/share/qt4 PATH=/usr/lib/x86_64-linux-gnu/qt4/bin:/usr/bin:/home/dargaud/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin qtcreator
```

---

