---
title: "Qt4 in Hardy too old?"
date: 2008-02-18
forum: Packaging and Compiling Programs
---

### Post by zegenie on 2008-02-18
Hi.

I'm trying to compile KDE4 from svn, which is somewhat a bold effort - but I've got it working, and up until the last few days, it built perfectly (well, as perfectly as you can expect when working with kdesvn). However - when trying to build kde4 today, it fails immediately, telling me that qt4 is too old - I've installed version 4.3.3, which is the latest in hardy, but it needs qt4 4.0.0. .. Anyone have any ideas where I can get it, or if it will be available in hardy anytime soon?

---

### Post by zegenie on 2008-02-19
Anyone?

---

### Post by Linicks on 2008-02-21
I update KDE4 svn each week, and just hit the same qt4.4.0 problem.

I guess they are now using the 'preview' version, which I am currently building.

[ftp://ftp.trolltech.com/qt/source/](ftp://ftp.trolltech.com/qt/source/)

And get the file:

qt-x11-preview-opensource-src-4.4.0-tp1.tar.gz

I hope it's the right one, anyway, as I cannot find any other.

Nick

---

### Post by zegenie on 2008-02-25
Thanks alot, downloading now ...

So this is not an official release library? Did you have any luck building it and compiling kde against it?

---

### Post by Linicks on 2008-02-26
Yes, it builds fine and KDE4 builds with it OK - but I am on Slackware, so I don't know if this will break anything on Ubuntu (I don't use KDE on my Ubuntu laptop).

I use the default install location and this ./configure line:

-nomake examples -nomake demos -qt-gif -no-exceptions -fast

It will install to:

/usr/local/Trolltech/Qt-4.4.0-tp1

which you will have specify to use in the KDE4 build environment.

Don't forget to set up the new QTDIR $ENV to point to the new location also.

Nick

---

