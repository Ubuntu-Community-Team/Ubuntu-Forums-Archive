---
title: "QT problem."
date: 2008-01-09
forum: Programming Talk
---

### Post by Kadrus on 2008-01-09
I have been having problems with QT..well I am having problems compiling some programs..I have everything installed...well at least I think I do..
[PHP]#include <QApplication>
#include <QPushButton>
int main(int argc, char *argv[])
{
QApplication app(argc, argv);
QPushButton hello("Test");
hello.resize(100, 30);
hello.show();
return app.exec();
 }[/PHP]
I am trying to compile this code..
I type:
qmake -project
qmake 
make
I have been getting the same error..which is driving me mad..
```

g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o ex.o ex.cpp
ex.cpp:1:24: error: QApplication: No such file or directory
ex.cpp:2:23: error: QPushButton: No such file or directory
ex.cpp: In function ‘int main(int, char**)’:
ex.cpp:6: error: ‘QApplication’ was not declared in this scope
ex.cpp:6: error: expected `;' before ‘app’
ex.cpp:8: error: ‘QPushButton’ was not declared in this scope
ex.cpp:8: error: expected `;' before ‘hello’
ex.cpp:9: error: ‘hello’ was not declared in this scope
ex.cpp:12: error: ‘app’ was not declared in this scope
ex.cpp: At global scope:
ex.cpp:4: warning: unused parameter ‘argc’
ex.cpp:4: warning: unused parameter ‘argv’
make: *** [ex.o] Error 1

```
Any help will be appreciated :)

---

### Post by Kadrus on 2008-01-09
Never mind..I got it to work..:)..Can any member staff close this..please..

---

### Post by LaRoza on 2008-01-09
> **Kadrus said:**
> Never mind..I got it to work..:)..Can any member staff close this..please..

Post the solution and mark it as solved? It would be helpful for future posters.

---

### Post by dwhitney67 on 2008-01-09
The solution was to fix his #include declarations.  The OP should have included the following:

[PHP]#include <qapplication.h>
#include <qpushbutton.h>[/PHP]

One of the things I find difficult to adapt to is that Qt defines their header files with names that differ from the class defined within.

---

