---
title: "Problems with QT build dependencies"
date: 2009-06-13
forum: Packaging and Compiling Programs
---

### Post by Kazade on 2009-06-13
I'm trying to package a program which uses QT 4. Although I can build the package using debuild, whenever I run pbuilder I get the following error:

```
checking for Qt... yes:
    QT_CXXFLAGS=-I/usr/include/qt4
    QT_DIR=
    QT_LIBS=-L/usr/lib -lQtCore -lQtGui -lQtOpenGL -lQtNetwork   -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi 
    QT_UIC=/usr/bin/uic-qt4
    QT_MOC=/usr/bin/moc-qt4
    QT_LRELEASE=/usr/bin/lrelease-qt4
checking correct functioning of Qt installation... failure
```

Has anyone seen this before? I'm obviously missing something from Build-Depends which exists on my machine, but I've no clue what it is!

---

### Post by asac on 2009-06-15
> **Kazade said:**
> I'm trying to package a program which uses QT 4. Although I can build the package using debuild, whenever I run pbuilder I get the following error:

```
checking for Qt... yes:
    QT_CXXFLAGS=-I/usr/include/qt4
    QT_DIR=
    QT_LIBS=-L/usr/lib -lQtCore -lQtGui -lQtOpenGL -lQtNetwork   -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi 
    QT_UIC=/usr/bin/uic-qt4
    QT_MOC=/usr/bin/moc-qt4
    QT_LRELEASE=/usr/bin/lrelease-qt4
checking correct functioning of Qt installation... failure
```

Has anyone seen this before? I'm obviously missing something from Build-Depends which exists on my machine, but I've no clue what it is!

There should be a config.log or something that might give hints on what is going wrong.

---

