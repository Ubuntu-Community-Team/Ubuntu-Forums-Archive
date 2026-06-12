---
title: "How does Ubuntu find c libraries, or, how I learned to stop worrying and love the Qt"
date: 2008-10-27
forum: Programming Talk
---

### Post by joesmith1234 on 2008-10-27
THIS IS A QUESTION ABOUT HEADERS AND COMPILERS.  NOT ABOUT QT.

Also, when reading this, please keep in mind that I'm fairly n00b to linux.  I'm running Ubuntu 8.04.

I was playing around with the qt tutorials.

I tried to add the following to the tutorial source:

```
#include <QGraphicsWidget>
```

The compiler says it can't find it.

I went and checked out a demo app that has that header included, the padnavigator.

The padnavigator example compiles fine, but the header declaration is different:
```
#include <QtGui/qgraphicswidget.h>
```

I try this header back in the tutorial, and the compiler still can't find the header.

I then tried comparing the two make files.

In my make there's:
```
INCPATH       = -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I.
```

In the padnavigator make there's:
```
INCPATH       = -I../../../mkspecs/linux-g++ -I. -I../../../include/QtCore -I../../../include/QtCore -I../../../include/QtGui -I../../../include/QtGui -I../../../include/QtOpenGL -I../../../include/QtOpenGL -I../../../include -I/usr/X11R6/include -I.moc/release-shared -I.uic/release-shared
```


Just FYI, the padnavigator code is located on my desktop:
```
/home/nibbles/Desktop/qt-x11-opensource-src-4.4.2/examples/graphicsview/padnavigator
```

So what I think is happening, is that qmake somehow automatically determines the location of the include paths when making the make file.  Is correct?

Next, the include path for the tutorial's makefile appears to be wrong.  When I do a "make install" from the source code located on my desktop, everything is installed to /usr/local/Trolltech/Qt-4.4.2/ and not /usr/include/qt4/ .  I assume the latter is the Qt version that was already on the system when I installed ubuntu.

How can I force the compilers and this qmake to build the makefile so it uses the libraries and headers for the new installation of Qt?

Note:  I also ran into this problem when I had compiled GStreamer.  All of my new code always ended up linking to the original GStreamer on the system at install.

:confused:

---

### Post by LaRoza on 2008-10-27
#include statements just include function prototypes and other non functioning code so the code can compile.

Linking is different and should be done on the command line (or IDE, if it can).

[http://doc.trolltech.com/3.3/tutorial1-01.html](http://doc.trolltech.com/3.3/tutorial1-01.html)

---

### Post by joesmith1234 on 2008-10-28
> **LaRoza said:**
> #include statements just include function prototypes and other non functioning code so the code can compile.

Linking is different and should be done on the command line (or IDE, if it can).

[http://doc.trolltech.com/3.3/tutorial1-01.html](http://doc.trolltech.com/3.3/tutorial1-01.html)

This problem isn't just with Qt, it also happens with GStreamer or anything I try to install from source.

I would take a wild guess that it has something to do with the way configure works.

Do I need to install the old versions of Qt, GStreamer, etc, before I try to compile a new one?

---

### Post by skullmunky on 2008-10-31
The base place GCC starts looking is /usr/include.  So when you say
```

#include <stdio.h>

```

that usually means /usr/include/stdio.h.

```

#include <qt4/Qt/QtGui/QGraphicsWidget>

```

would actually include /usr/include/qt4/Qt/QtGui/QGraphicsWidget

your 2 examples have tidier includes.  The way that works is in the Makefile, there's a -I directive to add other directories into the include path for GCC to search in.  

```

-I/usr/include/qt4/QtGui

```

means to search in that whole directory.  So you can just include QGraphicsWidget directly.

As to what the difference is between QGraphicsWidget and qgraphicswidget.h - NOTHING! 

```

more /usr/include/qt4/QtGui/QGraphicsWidget
#include "qgraphicswidget.h"

```

the one in caps just includes the other one.  This is some newfangled c++ convention that I don't really get but I think it's intended to make code more portable, so if necessary you could have QGraphicsWidget include slightly different things on different platforms but your app wouldn't have to change at all.

Yes, qmake should guess all the include directories correctly for you when it generates the makefile.

---

