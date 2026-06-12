---
title: "c/c++ graphics  libraries"
date: 2010-03-29
forum: Programming Talk
---

### Post by rajesh.kanakabandi on 2010-03-29
hi,
i'm new to programming in ubuntu. earlier i used to use windows and turoc3/ide. now i've moved to ubuntu cause of all the restrictions on windows.my problem is that many header files and libraries(graphics) in windows platform are not available here. somebody help me with some pleasant tutorial about the libraries and header files for c/c++ in ubuntu

thank you. :smile:

---

### Post by the_unforgiven on 2010-03-29
Ideally, you should be using one of the native windowing toolkits for X:
o. [QT]("http://qt.nokia.com/")
o. [gtk]("http://www.gtk.org/")
o. [wxWidgets]("http://www.wxwidgets.org/")
o. [SDL]("http://www.libsdl.org")

However, since it's very common for people to come over from TC, there is libgraph available. Read [this]("http://www.openpeta.com/index.php/2d-graphics-using-c-in-linux-graphics-h-in-linux/") for more.

Here is libgraph project page:
[http://savannah.nongnu.org/projects/libgraph](http://savannah.nongnu.org/projects/libgraph)

HTH ;)

---

### Post by dearingj on 2010-03-30
What kind of graphics are you looking to do? My personal favorite graphics library is [Irrlicht]("http://irrlicht.sf.net"), good mainly for 3D but it also has some 2D functions.

---

