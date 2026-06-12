---
title: "qt4 linkings and libaries?"
date: 2008-03-10
forum: Programming Talk
---

### Post by StOoZ on 2008-03-10
im trying to find the qt4 name to use with 'pkg-config' in order to know the linkings for compiling...
any idea?

and for next time, if I'll install a new type of libaries for something else, how do I know what to provide in 'pkg-config' to find the libs/linkings?


thanks.

---

### Post by WW on 2008-03-10
> 
$ pkg-config --list-all

will show all the packages that pkg-config knows about.

---

### Post by StOoZ on 2008-03-10
dude you are great!!
p.s:
Seems like I can find only this:
> guy@guy-desktop:/$ pkg-config --list-all | grep qt.*
qt-mt                       Qt - Libqt-mt.so.3.3.7 Library

no indication for qt4... hmm any idea why?
I've installed it.

---

### Post by StOoZ on 2008-03-10
tried also:
> guy@guy-desktop:/$ pkg-config --list-all | grep -i .*qt.*
qt-mt                       Qt - Libqt-mt.so.3.3.7 Library
QtGui                       Qtgui - Qtgui Library
QtSql                       Qtsql - Qtsql Library
QtNetwork                   Qtnetwork - Qtnetwork Library
QtScript                    Qtscript - Qtscript Library
QtTest                      QtTest - Qt Unit Testing Library
QtAssistantClient           Qtassistantclient - Qtassistantclient Library
QtXml                       Qtxml - Qtxml Library
QtUiTools                   Qtuitools - Qtuitools Library
QtCore                      Qtcore - Qtcore Library
QtOpenGL                    Qtopengl - Qtopengl Library
QtDBus                      QtDBus - Qt DBus module
QtSvg                       Qtsvg - Qtsvg Library
Qt3Support                  Qt3support - Qt3support Library


still no qt4.... :(

---

### Post by WW on 2008-03-10
[This link](http://packages.ubuntu.com/gutsy/i386/libqt4-dev/filelist) shows the list of files installed by the Ubuntu package **libqt4-dev**.  Scroll down to the file names that begin with /usr/lib/pkgconfig:
> 
/usr/lib/pkgconfig/Qt3Support.pc
/usr/lib/pkgconfig/QtAssistantClient.pc
/usr/lib/pkgconfig/QtCore.pc
/usr/lib/pkgconfig/QtDBus.pc
/usr/lib/pkgconfig/QtGui.pc
/usr/lib/pkgconfig/QtNetwork.pc
/usr/lib/pkgconfig/QtOpenGL.pc
/usr/lib/pkgconfig/QtScript.pc
/usr/lib/pkgconfig/QtSql.pc
/usr/lib/pkgconfig/QtSvg.pc
/usr/lib/pkgconfig/QtTest.pc
/usr/lib/pkgconfig/QtUiTools.pc
/usr/lib/pkgconfig/QtXml.pc

Are you sure that "qt4" is the name you want to use with pkg-config?  Figure out what part(s) of qt4 you are using, and try using the appropriate pkg-config command for it.

---

### Post by StOoZ on 2008-03-10
that was suppppppper useful!!!!
at least now I know where to dig with 'pkg-config' to get a proper compiling info for each library.
btw , this /usr/lib/pkgconfig  will hold all the proper libraries (or whatever it is..)
that are installed on a certain computer?

---

### Post by WW on 2008-03-10
I can't give an authoritative answer, but the Ubuntu package containing the development version of a library *should* put its pkg-config file, if it has one, in /usr/lib/pkgconfg.  However, I don't know if every library has a .pc file, so there might be some libraries that pkg-config will not know about.

Also, if you install a library from source (i.e. you compile it yourself with, for example, the usual "./configure, make, make install" commands), it will put its .pc file (if it has one) in /usr/local/lib/pkgconfig (unless you specified a different installation destination with the --prefix option to the configure script).

---

