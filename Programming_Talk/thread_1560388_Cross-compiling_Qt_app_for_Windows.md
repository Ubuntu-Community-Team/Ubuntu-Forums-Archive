---
title: "Cross-compiling Qt app for Windows"
date: 2010-08-24
forum: Programming Talk
---

### Post by Volt9000 on 2010-08-24
I'm writing an application whose ultimate target platform will be Windows. But I'm developing in Linux because I really need to get more used to it.

So through Googling I found [this article]("http://silmor.de/39") on how to cross-compile. A got a little annoyed when I was searching for those source packages, since they're buried within subfolders of subfolders on MingW's sourceforge page. I then had an "I'm an idiot" moment when I realized I could just search through Ubuntu's repos.

Well, one thing led to another, and I found [this repo source]("https://launchpad.net/~clazzes.org/+archive/ppa") which seems to have exactly what I want. There's only 2 problems with it:

1) It compiles to Qt 4.7.0, which at the time of this writing, hasn't yet been finalized
2) It doesn't work

Now of course, the second point is more important than the first. :)
More specifically, here's what happens:

I run i686-pc-mingw32-qmake-qt4, which generates my Makefile. I then run make, and here's my output:

```

make -f Makefile.Release
make[1]: Entering directory `/home/andrew/code/test'
i686-pc-mingw32-g++ -c -O2 -g -Wall --param=ssp-buffer-size=4 -mms-bitfields -O2 -frtti -fexceptions -mthreads -Wall -DUNICODE -DQT_LARGEFILE_SUPPORT -DQT_DLL -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_THREAD_SUPPORT -I'/usr/i686-pc-mingw32/mingw/include/QtCore' -I'/usr/i686-pc-mingw32/mingw/include/QtGui' -I'/usr/i686-pc-mingw32/mingw/include' -I'.' -I'/usr/i686-pc-mingw32/mingw/include/ActiveQt' -I'release' -I'.' -I'/usr/i686-pc-mingw32/share/qt4/mkspecs/mingw-w32-cross' -o release/main.o main.cpp
main.cpp:1:30: error: QtGui/QApplication: No such file or directory
In file included from main.cpp:2:
mainwindow.h:4:23: error: QMainWindow: No such file or directory
In file included from main.cpp:2:
mainwindow.h:10: error: expected class-name before ‘{’ token
mainwindow.h:11: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
mainwindow.h:12: error: expected ‘;’ before ‘public’
mainwindow.h:17: error: ‘QEvent’ has not been declared
mainwindow.h:22: error: expected ‘:’ before ‘slots’
mainwindow.h:23: error: expected primary-expression before ‘void’
mainwindow.h:23: error: ISO C++ forbids declaration of ‘slots’ with no type
mainwindow.h:23: error: expected ‘;’ before ‘void’
main.cpp: In function ‘int main(int, char**)’:
main.cpp:6: error: ‘QApplication’ was not declared in this scope
main.cpp:6: error: expected ‘;’ before ‘a’
mainwindow.h:14: error: ‘MainWindow::~MainWindow()’ is private
main.cpp:7: error: within this context
main.cpp:8: error: ‘class MainWindow’ has no member named ‘show’
main.cpp:9: error: ‘a’ was not declared in this scope
make[1]: *** [release/main.o] Error 1
make[1]: Leaving directory `/home/andrew/code/test'
make: *** [release] Error 2

```

There's no problem with the program; it's a barebones GUI app that compiles and runs fine natively on Linux.

Now, it's pretty obvious from the first error, the proper include path isn't present. Why is this? I would figure upon installation, the qmake.conf file would contain all the proper information.

I really don't want to have to manually edit my Makefile to add in all necessary include paths.

Is there some way I can fix this?

---

### Post by Volt9000 on 2010-08-25
*bump*

Can anyone help with this?

---

### Post by Volt9000 on 2010-08-26
*bump*

---

