---
title: "How to configure Qt4"
date: 2007-05-24
forum: Programming Talk
---

### Post by Ram Crammer on 2007-05-24
I have some C/C++ programming experience (4 years professionally).
I've used Qt3 on an old Mandrake GNU/Linux system, so I thought it
would be easy to use Qt on Ubuntu.  It appears that Synaptic does not
install a working Qt3 setup in Feisty, but just the minimal support
for apps that need the dynamic libraries.  So I thought I'd try Qt4.
As far as I can tell, everything seems to be installed, but the
compiler (g++) can't seem to find the headers properly.

I've been trying to build the example hello_world.cpp program with qt4.
I've tried setting up the environment with QTDIR=/usr/include/qt4, and
QTDIR=/usr/include/qt4/Qt, and setting my $PATH to include
/usr/share/qt4/bin.  Since g++ still doesn't find the headers, I tried
specifying the same include directories using the -I option, and of
course specifying the library with -l qt.  Nothing seems to work.  I
simply cannot get g++ to find the headers.  With the command shown, It spits out the following errors:

$ g++ hello_world.cpp -I /usr/include/qt4/Qt -l qt -o hello_world

In file included from hello_world.cpp:1:
/usr/include/qt4/Qt/qapplication.h:27:37: error: QtCore/qcoreapplication.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:28:31: error: QtGui/qwindowdefs.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:29:27: error: QtCore/qpoint.h: No such file or directory  
...etc. etc.

Please, what am I doing wrong or not doing?

---

### Post by seamless on 2007-05-24
I would recommend you use [qmake]("http://doc.trolltech.com/4.2/qmake-manual.html") to handle the actual complication command for you.

Here is a simple example:
```
TEMPLATE = app
LANGUAGE = C++
CONFIG += qt
HEADERS = mainwindow.h \
	tabthingy.h
SOURCES = main.cpp \ 
	mainwindow.cpp \
	tabthingy.cpp
```

Save that as <the name of the application>.pro replacing the .h and .cpp with the ones in your application. Now run qmake. Qmake will then create a Makefile for your environment. Run make and your application will be compiled.

---

### Post by Ram Crammer on 2007-05-24
Thanks Seamless!  I realize I can use qmake as you suggest, but for small, single file programs, it's much simpler to just use the command line.  However, I am beginning to suspect this may not be possible anymore, with the Qt directories set up as they are in Ubuntu.  Another possibility is to edit the #include precompiler directives to point to the corresponding header directory.  For example, instead of...

#include   <QApplication>

edit it to this:

#include  <QtGui/QApplication>

then include the slash / at the end of the include path on the command line with -I, invoking  g++ as follows:

$ g++ my_prog.cpp -I /usr/include/qt4/  -L qt -o my_prog  

This seems a little easier than setting up a .pro file.   I just thought there was an even easier way.  But I have searched the online docs and the O'Reilly book, "Programming with Qt", and could find no simple command line solution.  I can learn to live with this, and .pro files are certainly the way to go with any less trivial project.  

Does anyone else have a simple suggestion for how to tell g++ to look for headers in the ENTIRE directory subtree under /usr/include/qt4/  ?   I see there is also a link pointing to this directory, at /usr/share/qt4/include/, so this will also work as the command line specification to the -I option, as long as each #include is edited to add the parent dir of the header file as shown above.  

From my reading I think the /usr/include/qt4/QtGui and /usr/include/qt4/QtCore directories are supposed to be known to the compiler somehow, by default.  I haven't figured out if this is so, and don't see how it can be, unless there is a config file or environment variable (CONFIG)? that g++ looks at.  Does anyone know more about this?

Seeing how few replies are being posted to the Forum Programming Section, I am quite impressed that anyone took time to help.  Thanks very much and hope I can return the favor some time.

---

### Post by khedron on 2007-05-27
Did you find the answer to your question?

I was playing around, as I got similar errors following Trolltech's own tutorial ([http://doc.trolltech.com/4.1/tutorial-t7.html](http://doc.trolltech.com/4.1/tutorial-t7.html)).

I noticed that the tutorial was for qt4, but I had qt3 installed on my system. I installed qt4-dev-tools, but the default version of qmake was unaffected. So I called qmake-qt4:
```
qmake-qt4 -project; qmake-qt4; make
```This stopped my compilation errors. I'm only a noob at this sort of thing, so I'm not sure whether you have already tried this, but I hope this helps.

---

