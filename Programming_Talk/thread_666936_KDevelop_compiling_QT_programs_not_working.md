---
title: "KDevelop compiling QT programs not working"
date: 2008-01-13
forum: Programming Talk
---

### Post by reeseslover531 on 2008-01-13
ok so I am using the latest KDevelop.  I create a Basic QT4 application from under the QTMake project folder.  MY code is ```

#include <QApplication>
#include <QLabel>
int main(int argc, char *argv[])
{
QApplication app(argc,argv);
QLabel *label = new QLabel("Hello QT!");
label->show();
return app.exec();
}

```
and I run build project and it asks me to run qmake first, which I do, but then it spits out all these errors ```


cd '/home/joe/ta' && make -k 
cd src/ && make -f Makefile 
compiling main.cpp (g++)
main.cpp:22:24: error: QApplication: No such file or directory
main.cpp:23:18: error: QLabel: No such file or directory
main.cpp: In function ‘int main(int, char**)’:
main.cpp:26: error: ‘QApplication’ was not declared in this scope
main.cpp:26: error: expected `;' before ‘app’
main.cpp:27: error: ‘QLabel’ was not declared in this scope
main.cpp:27: error: ‘label’ was not declared in this scope
main.cpp:27: error: expected type-specifier before ‘QLabel’
main.cpp:27: error: expected `;' before ‘QLabel’
main.cpp:29: error: ‘app’ was not declared in this scope
main.cpp: At global scope:
main.cpp:24: warning: unused parameter ‘argc’
main.cpp:24: warning: unused parameter ‘argv’
make[1]: *** [main.o] Error 1
make[1]: Target `first' not remade because of errors.
make: *** [sub-src-make_default] Error 2
make: Target `first' not remade because of errors.
*** Exited with status: 2 ***

```
My problem is if I go into the folder of my project and run qmake-qt4 -project and then qmake-qt4 test.pro (which is the name of my project) and then run make, it complies and then runs fine.  What am I doing wrong??

---

### Post by dwhitney67 on 2008-01-13
Read, read, read...
[PHP]main.cpp:22:24: error: QApplication: No such file or directory
main.cpp:23:18: error: QLabel: No such file or directory[/PHP]

Try:

[PHP]#include <qapplication.h>
#include <qlabel.h>[/PHP]

---

### Post by daxumaming on 2008-03-19
got the same issue here. i had to delete all pro and makefiles and issue qmake manually before i got to compile a qt source. there seem to be some problem with KDevelop's way of creating a qmake project forcing us to manually do it. but that's ok since after that, everything worked without a hitch.

---

### Post by DanielArdelian on 2009-11-30
(1) Start a fresh Qt project (I tested this in a console app) and build it first
(2) Add these to a source file:
```

#include <QHostAddress>
...
QHostAddress adr;
...

```
(3) Try to rebuild it - you should get compile errors now
(4) Go to the ./src subdirectory of your project, edit src.pro in your favorite text editor, add this line and save it:
```

QT += network

```
(5) Now rebuild everything from KDevelop ( F8 ), it should work now

For more info, see this link: [http://doc.trolltech.com/4.5/qmake-project-files.html#declaring-qt-libraries](http://doc.trolltech.com/4.5/qmake-project-files.html#declaring-qt-libraries)

---

