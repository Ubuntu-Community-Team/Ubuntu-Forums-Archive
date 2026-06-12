---
title: "Qt5 packaging problem"
date: 2013-03-05
forum: Packaging and Compiling Programs
---

### Post by alenn on 2013-03-05
Hi guys

I have problems with Qt5 packaging. I included libs which are needed for common Qt5 application in mine control file but I get error those libs can't be installed. This is error:

pbuilder-satisfydepends-dummy : Depends: debhelper (>= 8.0.0) but it is not going to be installed
                                 Depends: qtbase5-dev but it is not installable
                                 Depends: qt5-qmake but it is not installable
                                 Depends: qtchooser but it is not installable


How can I solve this. I had no problems with Qt4.

---

### Post by alenn on 2013-03-06
bump

---

