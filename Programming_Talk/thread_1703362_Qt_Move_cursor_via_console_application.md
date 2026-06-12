---
title: "Qt: Move cursor via console application"
date: 2011-03-09
forum: Programming Talk
---

### Post by hakermania on 2011-03-09
This is the code but the program unexpectedly finishes at the line taht say s setPos(x,y) (segmentation fault). What do I do wrong?
```
#include <QtGui>
#include <QtCore>  //for any occasion, a lot of includes...
#include <QApplication>
int main()
{
    QCursor *cur = new QCursor;
    cur->setPos(0 ,0); //HERE it crashes
    return 0;
}

```
The project file is:```

QT -= gui

TARGET = curmove
CONFIG   += console
CONFIG   -= app_bundle

TEMPLATE = app


SOURCES += main.cpp
```

---

### Post by GeneralZod on 2011-03-09
From the [docs](http://doc.qt.nokia.com/latest/qcursor.html):

> 
Attempting to use a QCursor that was created before QApplication will result in a crash.


---

### Post by hakermania on 2011-03-11
So, how exactly should the code be???

---

### Post by hakermania on 2011-03-26
that's it:
```
#include <QtGui/QCursor>
#include <QApplication>

int main(int argc, char *argv[])
{
    QApplication a(argc, argv);
    QCursor *cur = new QCursor;
    cur->setPos(0,0);
    return 0;

    return a.exec();
}
```

---

