---
title: "compiling qt4 applications"
date: 2007-01-02
forum: Programming Talk
---

### Post by litnsio2 on 2007-01-02
Hello, i'm newbie programming in *nix environments.
I was trying to make a simple hello world program with qt4 but i couldn't.

here is the code i wrote:
---
 #include <QtGui/QApplication>
 #include <QtGui/QPushButton>
 
 int main(int argc, char *argv[])
 {
     QApplication app(argc, argv);
     QPushButton hello("Hello world!");
     hello.resize(100, 30);
 
     hello.show();
     return app.exec();
 }
---

when i 'qmake -project' and 'qmake' everything was fine. but when i tried to make it,
following error came out:

----
g++  -o tviewer hello.o    -L/usr/share/qt3/lib -L/usr/X11R6/lib -lqt-mt -lXext -lX11 -lm -lpthread
hello.o: In function `main':
hello.cpp:(.text+0x36): undefined reference to `QApplication::QApplication(int&, char**, int)'
hello.cpp:(.text+0x4a): undefined reference to `QString::fromAscii_helper(char const*, int)'
hello.cpp:(.text+0x67): undefined reference to `QPushButton::QPushButton(QString const&, QWidget*)'
hello.cpp:(.text+0x7f): undefined reference to `QString::free(QString::Data*)'
hello.cpp:(.text+0x111): undefined reference to `QString::free(QString::Data*)'
collect2: ld returned 1 exit status
----

they says ld cannot find proper library(or proper function in qt library) but i have qt-dev package installed!
i guess this code needs to be linked with libqt4, but theres no that stuff. here's files under /usr/lib/ which contains qt in their name.

---
thom@thom:~/code/tviewer$ ls /usr/lib/*qt*
/usr/lib/libavahi-qt3.so.1      /usr/lib/libqthreads.la
/usr/lib/libavahi-qt3.so.1.0.1  /usr/lib/libqthreads.so
/usr/lib/libqt-mt.la            /usr/lib/libqthreads.so.12
/usr/lib/libqt-mt.prl           /usr/lib/libqthreads.so.12.3.1
/usr/lib/libqt-mt.so            /usr/lib/libqthreads.so.9
/usr/lib/libqt-mt.so.3          /usr/lib/libqthreads.so.9.0.0
/usr/lib/libqt-mt.so.3.3        /usr/lib/libqtmcop.so.1
/usr/lib/libqt-mt.so.3.3.6      /usr/lib/libqtmcop.so.1.0.0
/usr/lib/libqthreads.a

/usr/lib/qt3:
plugins

/usr/lib/qt4:
plugins
--- 

what should i do to compile my first code?

and here's a another question, does 'libqt-mt-so.3.3.6' mean that the version of libqt-mt is 3.3.6?
if so, where's the qt4 library?



thanks in advance.


intaek.

ps. if you are capable of reading Korean text, please see [this page]("http://kldp.org/node/76802")

---

### Post by kaamos on 2007-01-02
Hello!

Make sure you have installed libqt4-dev.

---

### Post by litnsio2 on 2007-01-02
Surely i have that installed.

:)

---

### Post by llonesmiz on 2007-01-03
I'm no expert in qt, but seeing:

```
 g++  -o tviewer hello.o    -L/usr/share/**qt3**/lib -L/usr/X11R6/lib -lqt-mt -lXext -lX11 -lm -lpthread 
```makes me think that you are using qt3's qmake instead of the qt4's one.

If in a terminal you write:

```
 file `which qmake` 
```and it points to 
/usr/share/qt3/bin/qmake 

you can be sure that this is the problem.
In order to solve this you could use 
/usr/share/qt4/bin/qmake instead of simply qmake:

```
/usr/share/qt4/bin/qmake -project
/usr/share/qt4/bin/qmake
make
```Good luck.

PS: Looking at packages.ubuntu.com I've found that there is a qmake-qt4 in /usr/bin. Using that would save you from the mess above.

```
qmake-qt4 -project
qmake-qt4
make
```

---

### Post by litnsio2 on 2007-01-03
thanks. i can compile my code now.

happy new year~~!

:D

---

### Post by domino1241 on 2008-07-14
llonesmiz, you are a godsend.

Sometimes the answer is right in front of your nose.

Thanks!

---

