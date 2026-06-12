---
title: "Compilation problem, cmake and FreeCAD source code"
date: 2016-02-26
forum: Packaging and Compiling Programs
---

### Post by mslonik on 2016-02-26
Dear Forum,

I'm running the following distro:

```

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

```

Lately I tried to install FreeCAD application from sources ([ver. 0.15]("https://github.com/FreeCAD/FreeCAD/archive/0.15.tar.gz")). For compilation I've used CMake with the following syntax:

```
$ cmake -DFREECAD_USE_EXTERNAL_PIVY=1 -DCMAKE_BUILD_TYPE=Release .
```

The problem which I face at my machine is:

```

Run Build Command:/usr/bin/make "cmTryCompileExec1556370054/fast"
/usr/bin/make -f CMakeFiles/cmTryCompileExec1556370054.dir/build.make CMakeFiles/cmTryCompileExec1556370054.dir/build
make[1]: Wej&#347;cie do katalogu `/home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp/CMakeFiles 1
Building CXX object CMakeFiles/cmTryCompileExec1556370054.dir/CheckSymbolExists.cxx.o
/usr/bin/c++    -Wno-deprecated -Wno-write-strings  -I/usr/include/qt4    -o CMakeFiles/cmTryCompileExec1556370054.dir/CheckSymbolExists.cxx.o -c /home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp/CheckSymbolExists.cxx
/home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp/CheckSymbolExists.cxx: In function ‘int main(int, char**)’:
/home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp/CheckSymbolExists.cxx:8:19: error: ‘Q_WS_WIN’ was not declared in this scope
   return ((int*)(&Q_WS_WIN))[argc];
                   ^
make[1]: Opuszczenie katalogu `/home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp'
make[1]: *** [CMakeFiles/cmTryCompileExec1556370054.dir/CheckSymbolExists.cxx.o] B&#322;&#261;d 1
make: *** [cmTryCompileExec1556370054/fast] B&#322;&#261;d 2

File /home/maciej/FreeCAD-0.15/CMakeFiles/CMakeTmp/CheckSymbolExists.cxx:
/* */
#include <QtCore/qglobal.h>

int main(int argc, char** argv)
{
  (void)argv;
#ifndef Q_WS_WIN
  return ((int*)(&Q_WS_WIN))[argc];
#else
  (void)argc;
  return 0;
#endif
}

```

More information is attached to this message. My guess is that something is wrong with one of the qt packages. As I've already checked, the following location exists: /usr/include/qt4/QtCore and it is full of files, including qglobal.h, which keeps definition of Q_WS_WIN. What might be wrong?

Kind regards, mslonik

---

### Post by T.J. on 2016-02-26
From, what little I read, the Q_WS macros were dropped.  If you are using Qt5, this may help.  

[https://www.kdab.com/porting-from-qt-4-to-qt-5/](https://www.kdab.com/porting-from-qt-4-to-qt-5/)

" In Qt 5, the Q_WS_* macros have been removed, so any code wrapped in them will never be compiled. Where appropriate (ie when code being wrapped is operating system specific and not window system specific), such code can and should be ported to the Q_OS_* macros."

---

### Post by mslonik on 2016-02-26
Hi T.J.,

Thank you for your reply. As I've already checked, my version of qt:

```

$ qmake --version
QMake version 2.01a
Using Qt version 4.8.6 in /usr/lib/i386-linux-gnu

```

Kind regards, mslonik

---

### Post by T.J. on 2016-02-27
If you can please give me some specifics about what setup you are using - version of Linux  (Ubuntu or whatever), I'll run a set of test compiles for you and try to send you a fix.  I can't promise anything and it may take a few days to setup.  Please let me know if you are using x64 or x32.  I would prefer to take a closer look at this, before I offer further comments.

---

### Post by mslonik on 2016-02-27
I've shared my doubts about compilation problem at FreeCAD forum. People there advised me to not continue my attempts to compile this specific version of FreeCAD. In their opinion this approach is ineffective as version 0.15 is very outdated and because of that I may face serious problems with dependencies. What's more, even if compilation would be successful, it not necessarily push me to solution of specific problem related to usage of this application. Another words my idea to compile this version of application is dead end. Therefore I propose to close this thread. Thank you for your time and support.

Kind regards, mslonik

---

### Post by T.J. on 2016-02-27
As you wish, but may I might offer an alternative suggestion before you close it that might suit your aims?  Compiling older software on the normal version of Ubuntu is like trying to hit a moving target.  If you do need to compile it, it should be much easier to compile on an older version or LTS version. You can make that possible with a KVM.  You can always host a KVM, inside your existing Linux, and install an older OS with FreeCAD in it.  It's the ultimate compatibility feature. The KVM will also shield your main installation from any patch or security concerns when using the older software.  It's the best of both worlds without the pain.

I use KVM's for Steam and for Windows especially (which I do not trust since v10.)  If you need help getting setup or passing data from host and back, please let me know I'd be happy to lend a hand.

---

### Post by mslonik on 2016-02-27
Thank you for your proposal. Good to know about KVM opportunity. To be honest I've forgotten about this one. I sustain my previous opinion about dead end in this particular scenario. Let's close this thread. Again, thank you for your support, T.J.!

---

### Post by T.J. on 2016-02-28
You're very welcome. Please consider the offer open-ended.  If you change your mind, please send me a PM.

---

