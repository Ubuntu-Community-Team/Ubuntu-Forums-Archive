---
title: "Annoying QT4 compile problem"
date: 2010-02-07
forum: Programming Talk
---

### Post by Woody1987 on 2010-02-07
Im working on a project that uses alot of QT4. The problem i have is that when i try to compile i get the following error:

> /usr/include/qt4/QtCore/QtCore:3: In file included from /usr/include/qt4/QtCore/QtCore:3,
/usr/include/qt4/QtGui/QtGui:3: from /usr/include/qt4/QtGui/QtGui:3,
/home/matt/Dropbox/ParticleSimulator/window.h:6: from window.h:6,
/home/matt/Dropbox/ParticleSimulator/window.cpp:2: from window.cpp:2:
/usr/include/qt4/QtCore/qtextcodec.h:52: error: expected initializer before &#8216;QtCoreModule&#8217;

Im coding this within qt-creator. The weird thing is, is that it was working fine yesterday but since trying to recompile today without making ANY changes it refuses to work. Any solution?

---

### Post by Funnnny on 2010-02-07
It should be something weird with your header include.
check the include <qtextcodec.h> and move around abit to find the extract problem

---

### Post by Woody1987 on 2010-02-07
> **Funnnny said:**
> It should be something weird with your header include.
check the include <qtextcodec.h> and move around abit to find the extract problem

I havent got <qtextcodec.h> included, the error seems to be with <QtGui> so i moved that around and it didnt help.

---

### Post by Woody1987 on 2010-02-07
fixed it

---

### Post by mdurham on 2010-02-07
> **Woody1987 said:**
> fixed it
how?

---

### Post by Woody1987 on 2010-02-08
> **mdurham said:**
> how?

I have a header which i use to store some global variables such as:

extern QString name;
extern int age;
etc

problem was, was that i had an extern QString without a name which caused the problem so my header looked like:

extern QString name;
extern int age;
extern QString

I simply removed the last one and it worked.

---

### Post by afrodeity on 2010-03-08
Sorry to bother, slightly off topic, but what do I have to install to compile with QT?

My headers are installed but I get this error:
[CODE}
Could NOT find QtCore header
[/CODE]

---

### Post by Zugzwang on 2010-03-08
You might obtain better answers if you write where you get this error message under which circumstances. For the time being, install the "libqt4-dev" package:
```

sudo apt-get install libqt4-dev

```

---

### Post by afrodeity on 2010-03-08
No problem, I fixed it by installed the QT dev packages in Synaptic. The message is misleading, the linux headers were installed, the core-dev wasn't.

---

