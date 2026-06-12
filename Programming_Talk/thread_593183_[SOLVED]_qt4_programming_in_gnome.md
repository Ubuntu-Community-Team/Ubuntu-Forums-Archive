---
title: "[SOLVED] qt4 programming in gnome"
date: 2007-10-26
forum: Programming Talk
---

### Post by rbprogrammer on 2007-10-26
ok, so i am making a qt4 program in gnome.  but when i go to compile a simple hello world program, i get errors.

this is the program i am trying to compile:
```

#include <QApplication>
#include <QPushButton>
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    qDebug("Hello from Qt 4!");

    QPushButton hello("Hello world!");
    hello.resize(100, 30);

    hello.show();
    return app.exec();
}

```
and then this is what commands i used to compile:
```

$ qmake -project
$ qmake
$ make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o main.o src/main.cpp
src/main.cpp:1:24: error: QApplication: No such file or directory
src/main.cpp:2:23: error: QPushButton: No such file or directory
src/main.cpp: In function ‘int main(int, char**)’:
src/main.cpp:6: error: ‘QApplication’ was not declared in this scope
src/main.cpp:6: error: expected `;' before ‘app’
src/main.cpp:7: error: ‘qDebug’ was not declared in this scope
src/main.cpp:9: error: ‘QPushButton’ was not declared in this scope
src/main.cpp:9: error: expected `;' before ‘hello’
src/main.cpp:10: error: ‘hello’ was not declared in this scope
src/main.cpp:13: error: ‘app’ was not declared in this scope
src/main.cpp: At global scope:
src/main.cpp:4: warning: unused parameter ‘argc’
src/main.cpp:4: warning: unused parameter ‘argv’
make: *** [main.o] Error 1

```
i installed libqt4-dev, which installed quite a few other programs, but i suspect that the program is trying to use qt3 headers but i need to use the qt4.

what should i do so that i can compile qt4 programs??

---

### Post by rbprogrammer on 2007-10-27
ok, i figured it out..

in case anyone else ever has the same problem, this is what i did:
[INDENT]
**uninstall:**
libqt3-headers
libqt3-mt-dev
qt3-dev-tools

**intalled:**
libqt4-core
libqt4-dev
libqt4-qt3support
qt4-dev-tools
[/INDENT]

when installing the needed qt4 packages, some other were installed automatically because of the dependencies, so i didnt mention them.

***NOTE:**
Do not uninstall libqt3-mt as it is the qt3 runtime binary libraries.  i did not uninstall this because then some of my other programs would be removed.  like amarok, kaffeine, etc..

---

### Post by marsteel on 2007-10-27
```
$/usr/bin/qmake-qt4 -project
$/usr/bin/qmake-qt4
$make
```

:guitar:

---

