---
title: "installing qt3"
date: 2005-12-16
forum: Programming Talk
---

### Post by grim918 on 2005-12-16
can anyone help me out with installing qt3 for use with C++.
and does anyone know how i can make it work with my anjuta ide.
id appreciate any help

---

### Post by psychicdragon on 2005-12-16
To get the qt3 headers etc. is as simple as:```
sudo apt-get install qt3-dev-tools
```I've never used anjuta, so I can't say for certain, but I don't think development with qt is possible. There is an IDE called kdevelop which I think most KDE people use.

---

### Post by grim918 on 2005-12-17
i installed the qt3 headers with sudo apt-get install qt3-dev-tools.

i also created a simple hello program to test the qt3 installation.
here is the program:

#include <qapplication.h>
#include <qlabel.h>
int main(int argc, char *argv[])
{
  QApplication app(argc, argv);
  QLabel *label = new QLabel("Hello Qt!", 0);
  label->show();
  return app.exec();
}

when i try to compile the program using g++ i get this error:

becky@ubuntu:~/Desktop$ g++ hello.cpp
hello.cpp:1:26: error: qapplication.h: No such file or directory
hello.cpp:2:20: error: qlabel.h: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:6: error: ‘QApplication’ was not declared in this scope
hello.cpp:6: error: expected `;' before ‘ap’
hello.cpp:7: error: ‘QLabel’ was not declared in this scope
hello.cpp:7: error: ‘label’ was not declared in this scope
hello.cpp:7: error: expected type-specifier before ‘QLabel’
hello.cpp:7: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope

can someone please help me out.

---

### Post by toojays on 2005-12-17
You need to set up your project so that gcc knows where to find the Qt headers. I don't know how ajunta does it, but you need to get it to put "-I/usr/include/qt3" into the gcc command line. You will also need to tell gcc to link to the Qt libs.

---

### Post by grim918 on 2005-12-18
im using g++, and does anyone know how i can the compiler to look in the right location. and how do i get it to link. im new to linux and could really use some help. im used to microsoft which pretty much does everything for you. thanks to everyone that has been helping me.

---

### Post by asimon on 2005-12-19
It's easy if you use qmake. Just make an qmake project file, which is trivial for your example. Just put
```
SOURCES = hello.cpp
CONFIG += qt warn_on release
``` into hello.pro .
Then generate a Makefile with qmake from the project file:
```
$ qmake -o Makefile hello.pro
```
qmake will handle all needed paths and linker options etc. and generates a working makefile. To build your program just call make:
```
$ make
```

Of course you can also do without qmake, i.e. something like
```
$ g++ -I/usr/include/qt3 -L/usr/share/qt3/lib -L/usr/X11R6/lib -lqt-mt -lXext -lX11 -lm -lpthread hello.cpp
```

For more information on qmake have a look at the [qmake User guide](http://doc.trolltech.com/3.3/qmake-manual.html) and for a quick start the [10 minute guide to using qmake](http://doc.trolltech.com/3.3/qmake-manual-3.html).

EDIT:
Another option is to use [kdevelop](http://www.kdevelop.org/) (which can be found as kdevelop3 in universe). There you can create projects via GUI dialogs, which can make it easier to get a start.

---

