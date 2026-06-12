---
title: "Ubuntu 11.10: Qt Creator can't locate QApplication header and include it"
date: 2011-10-22
forum: Programming Talk
---

### Post by veroslav on 2011-10-22
Hi,

I am trying to start developing QT applications on Ubuntu 11.10, and I downloaded and installed Qt Creator (v 2.2.1, based on Qt 4.7.3) from the Software Center. 

The following add-ons were also installed: gdb, qt4-demos, qt4-dev-tools, qt4-doc, qt4-qmlviewer and qtcreator-doc.

I try creating a new project in Qt Creator like this:

Create project...->Other Project->Qt Console Application

In the main.cpp that is created, however, if I try to include simple headers like:

```
#include <QApplication>
```then the Qt Creator complains about:

```
QApplication: No such file or directory
```I can include headers like this one though:

```
#include <QtCore/QCoreApplication>
```Under Tools->Options->Qt4, I can see that the path to qmake-qt4 is auto-detected and set as:

/usr/bin/qmake-qt4

What am I missing in order to get Qt Creator to find QApplication header?

Thanks in advance.

Kind Regards,
Veroslav

---

### Post by veroslav on 2011-10-22
Please ignore the question above; I choose Qt Gui Application when creating a new project instead, and everything is fine.

I consider this issue solved.

---

