---
title: "qt4 and KDevelop"
date: 2007-06-13
forum: Programming Talk
---

### Post by Redscare on 2007-06-13
Hello again. I have just recently transitioned from Windows .Net GUI programming to the universal qt4, but I have already run into a huge problem: I am using the KDevelop IDE. I have the qt4-dev libraries installed, and I tell KDevelop to use qmake-qt4. Here is the problem. When I write this code:
```
#include<QApplication>
```
The compiler tells me that QApplication was not found. I am forced to write
```
#include<QtGui/QApplication>
```
for the code to compile. This is not too bad, but I end up having to search everywhere for any additional headers (for example QLabel). Please, how can I fix this? Thanks in advance.

---

### Post by g8m on 2007-06-14
As far as I know, include <QtGui> should be enough to include all gui components. Adding sql supports needs another <QtSql> include.

---

### Post by Redscare on 2007-06-14
But is there any reason that I cannot include QApplication, as it says on the trolltech site?

---

### Post by Redscare on 2007-06-14
I figured it out: it was a QT -= gui entry in the .pro file.

---

