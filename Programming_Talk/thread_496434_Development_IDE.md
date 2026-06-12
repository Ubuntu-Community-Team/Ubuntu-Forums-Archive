---
title: "Development IDE"
date: 2007-07-09
forum: Programming Talk
---

### Post by sfarber on 2007-07-09
Hello.
I am a C++ & MFC Programmer.
I was just moving to Linux (Ubuntu).

How can I get Documentation on the equivalent MFC on linux?
What IDE for C++ there is for Linux?

Thanks,
Shay.

---

### Post by j_g on 2007-07-09
If you're looking for a Linux equivalent to Microsoft's IDEs, then you're going to be in for a big disappointment. Linux IDEs are all built on top of the extremely dreadful GNU autotools, and consequently suffer from a severe "disconnect" between the user interface, and the compiler/linker. Don't expect a Linux IDE that is going to prevent you from having to hand-edit make files anyway. So you may as well forget the IDE altogether and learn how to write a simple makefile.

---

### Post by luisromangz on 2007-07-09
Well, there are a number of IDEs, like Anjuta, or KDevelop. As a KDE user, I have mainly used KDevelop, and I found it quite good.

Bye.

---

### Post by Smygis on 2007-07-09
[http://www.gtkmm.org/](http://www.gtkmm.org/)
or perhaps [http://www.wxwidgets.org/](http://www.wxwidgets.org/)

And for IDE,
Nice IDE's: Code::Blocks (Nightly build), Geany and perhaps some more.

---

### Post by kknd on 2007-07-09
wxWidgets + Code::Blocks nightly build rocks!

---

### Post by the_unforgiven on 2007-07-09
KDevelop is much like Visual Studio - in the look and feel, I mean...
Personally, I don't like to use IDEs that much because they end up bloating the build process too much.
Hand-crafted Makefiles is my way ;)
But, to start off, you might feel homely with KDevelop - it uses almost the same metaphors as VS.
Then, as you understand the build process on linux, you might want to write makefiles yourself.

HTH ;)

---

### Post by pmasiar on 2007-07-09
J_g is back in his old game again: whining how bad Linux is for developers. Don't get discouraged, ignore him, and learn do it the Linux way.

---

### Post by destructchaos on 2007-07-09
i used Kdev when learning QT in a class last semester.  i worked pretty well and was easy to pick up, coming from VS 6, though i had to make minor tweaks to the make files so my idiot professor could run my projects on the god-forsaken hack known to the world as cygwin.

---

### Post by math on 2007-07-09
Try netbeans with c/c++ plugin. It's very nice.

---

### Post by bulldog060 on 2007-07-10
I personally like Eclipse with teh CDT addon ...  [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

---

### Post by Golly on 2007-07-11
Hello luisromangz,
you wrote:
> As a KDE user, I have mainly used KDevelop, and I found it quite good.

Yesterday I have installed kdevelop with synaptic. So, I think, all depencies are good.
But when I try to build a qmake-application, there is an error.
> cd '/home/bu/mytest' && QTDIR="/usr/share/qt3" make -j1 
cd src && make -f Makefile
make[1]: Betrete Verzeichnis '/home/bu/mytest/src'
qmake -o Makefile src.pro
make[1]: Verlasse Verzeichnis '/home/bu/mytest/src'
make[1]: Betrete Verzeichnis '/home/bu/mytest/src'
g++ -c -pipe -Wall -W -O2 -D_REENTRANT -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../src -I/usr/include/qt3 -o mytest.o mytest.cpp
make[1]: g++: Kommando nicht gefunden
make[1]: *** [mytest.o] Fehler 127
make[1]: Verlasse Verzeichnis '/home/bu/mytest/src'
make: *** [sub-src] Fehler 2
*** Exited with status: 2 ***


When I search for "g++" with "slocate" there is no response,
When I lock in synaptic, there are g++-3.4 installed.

What is wrong?
Sorry for my bad english!
Bye Golly

---

### Post by ButteBlues on 2007-07-11
Install the package 'build-essential' in Synaptic.

---

