---
title: "Access qt objects from code on a form made in qt designer"
date: 2011-04-23
forum: Programming Talk
---

### Post by Hansmc on 2011-04-23
I made a form with tabs on it, in qt designer, and on one of the tabs I have a QListWidget called listWidget. I made this project in netbeans, so it made a wrapper class for my top level widget. In the constructor that it set up for me, I am trying to populate the list. But it cannot find it. It just says there is no widget with that name. I am not  sure how to go about accessing it. I assume that it is in some sub name space or widget, but I cannot figure out how to access widgets in the tabs of the tab widget. As you can see I am very much a beginner at this. Thanks for any help.

---

### Post by Vaphell on 2011-04-24
try QObject methods to access children

const QObjectList & children () const
T findChild ( const QString & name = QString() ) const
QList<T> findChildren ( const QString & name = QString() ) const
QList<T> findChildren ( const QRegExp & regExp ) const

[http://doc.qt.nokia.com/latest/qobject.html](http://doc.qt.nokia.com/latest/qobject.html)

---

