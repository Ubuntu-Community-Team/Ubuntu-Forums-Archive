---
title: "Qt development  problem"
date: 2006-12-19
forum: Programming Talk
---

### Post by ddtrust on 2006-12-19
Hi,

I have problems running make after creating the MakeFile with qmake:

```
jk@desktop:~/myprograms/c/QtTest$ qmake -o Makefile metric.pro
jk@desktop:~/myprograms/c/QtTest$ make
/usr/share/qt3/bin/uic conversionform.ui -o .ui/conversionform.h
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
as: unrecognized option `-Qy'
make: *** [.obj/main.o] Error 2
jk@desktop:~/myprograms/c/QtTest$
```

I think this has something to do with installation or environment variable problems? Can anyone help me. This is the first time I've tested Qt, so please be gentle. ;)

---

### Post by ddtrust on 2006-12-19
Ooops.. this post was rubbish.. :)

---

### Post by ddtrust on 2006-12-20
> **ddtrust said:**
> Hi,

I have problems running make after creating the MakeFile with qmake:

```
jk@desktop:~/myprograms/c/QtTest$ qmake -o Makefile metric.pro
jk@desktop:~/myprograms/c/QtTest$ make
/usr/share/qt3/bin/uic conversionform.ui -o .ui/conversionform.h
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
as: unrecognized option `-Qy'
make: *** [.obj/main.o] Error 2
jk@desktop:~/myprograms/c/QtTest$
```

I think this has something to do with installation or environment variable problems? Can anyone help me. This is the first time I've tested Qt, so please be gentle. ;)

This is still not working.. any help?

---

### Post by ddtrust on 2006-12-21
I noticed that I have to run make as root. Any clues how to get rid of this?

---

### Post by Hendrixski on 2007-08-01
sudo make will run it under root priveledges without you having to be root.

Many things you don't want to be done with root priveledges, sometimes you'll want to fake it, so use fakeroot.

like fakeroot dpkg-buildpackage for packaging stuff for Ubuntu... which is arguably a better way of installing things than running make, make install... because you'll probably delete the makefile so you can't run make uninstal.. but if it's packaged you'll always be able to run apt-get remove YourPackage

---

