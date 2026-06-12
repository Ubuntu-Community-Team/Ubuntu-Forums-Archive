---
title: "Qt4 errors"
date: 2008-10-31
forum: Programming Talk
---

### Post by kashthealien on 2008-10-31
Hello every one, I am new to LINUX/ubuntu and QT4 programming, I installed then necessary libraries qt4lib-core qt4lib-gui, qt4lib and so on..

I tried a hello world program.

#include <qt4/QtGui/qapplication.h>
#include <qt4/QtGui/qpushbutton.h>


int main( int argc, char **argv )
{
    QApplication a( argc, argv );

    QPushButton hello( "Hello world!", 0 );
    hello.resize( 100, 30 );

    a.setMainWidget( &hello );
    hello.show();
    return a.exec();
}

but I couldn't compile because of errors. which were as follows


/usr/include/qt4/QtGui/qapplication.h:47:37: error: QtCore/qcoreapplication.h: No such file or directory
/usr/include/qt4/QtGui/qapplication.h:48:31: error: QtGui/qwindowdefs.h: No such file or directory
/usr/include/qt4/QtGui/qapplication.h:49:27: error: QtCore/qpoint.h: No such file or directory
/usr/include/qt4/QtGui/qapplication.h:50:26: error: QtCore/qsize.h: No such file or directory
/usr/include/qt4/QtGui/qapplication.h:51:27: error: QtGui/qcursor.h: No such file or directory
In file included from hello.cpp:8:
/usr/include/qt4/QtGui/qpushbutton.h:47:35: error: QtGui/qabstractbutton.h: No such file or directory
In file included from hello.cpp:7:
/usr/include/qt4/QtGui/qapplication.h:64: error: ‘QT_BEGIN_HEADER’ does not name a type
/usr/include/qt4/QtGui/qapplication.h:84: error: function definition does not declare parameters
/usr/include/qt4/QtGui/qapplication.h:363: error: ‘QT_END_HEADER’ does not name a type
In file included from hello.cpp:8:
/usr/include/qt4/QtGui/qpushbutton.h:57: error: function definition does not declare parameters
hello.cpp:11: error: expected constructor, destructor, or type conversion before ‘int’

There is a folder called /usr/include/qt4 which has the folders QtGui etc.
what should I do to remove the errors

---

### Post by snova on 2008-10-31
Add these flags to the compiler invocation:

```
-I/usr/include/qt4 -I/usr/include/qt4/Qt -I/usr/include/QtCore -I/usr/include/QtGui
```

I'm honestly not certain if the last two are necessary. They probably are...

Includes should be "QtGui/QApplication". Do not use the qt4/ prefix, that's an installation thing.

---

### Post by kcode on 2008-10-31
You can directly use qmake for compiling, like this:
(first cd into the directory where your .c file exists)
```

qmake -project
qmake
make

```

which will produce an executable file.

---

### Post by samjh on 2008-10-31
> **kashthealien said:**
> I tried a hello world program.

#include <qt4/QtGui/qapplication.h>
#include <qt4/QtGui/qpushbutton.h>


int main( int argc, char **argv )
{
    QApplication a( argc, argv );

    QPushButton hello( "Hello world!", 0 );
    hello.resize( 100, 30 );

    a.setMainWidget( &hello );
    hello.show();
    return a.exec();
}

First of all, your inclusion headers are wrong.

They should be:
```
#include <QApplication>
#include <QPushButton>
```

The setMainWidget() function was deprecated in Qt4. :)  You should remove it if you're using Qt4.

Your code should read like this:
```
#include <QApplication>
#include <QPushButton>

int main(int argc, char **argv)
{
    QApplication a(argc, argv);

    QPushButton hello("Hello world!", 0);
    hello.resize(100, 30);

    hello.show();
    return a.exec();
}
```

The QPushButton constructor sets the parent parameter as 0 by default, so for your program you can just use [FONT="Courier New"]QPushButton hello("Hello world!");[/FONT]

And very importantly, use qmake to build you program, like what Kcode posted above.  Name your program's source file as main.cpp and run these commands to build it:
```
qmake -project
qmake
make
```

---

### Post by kashthealien on 2008-11-01
It worked after I used 
Qmake -project
Qmake
make

Thanks a lot everyone.:)

---

### Post by Cantonel on 2008-11-12
I'm new to this whole ubuntu thing. Where would you type qmake?

---

### Post by BackwardsDown on 2008-11-12
In the commandline in the directory where your source is.

---

