---
title: "What needs to be set to build the Qt designer projects"
date: 2007-04-09
forum: Programming Talk
---

### Post by abickerton on 2007-04-09
I've got both Qt 3.3.6 & Qt4 + compatibiity headers installed and I still cannot build the examples from the documentation iin QtDesigner.

I've tried : 
```

export QTDIR=/usr/share/Qt3
export PATH=$PATH:$QTDIR/bin

```

On trying to build the first tutorial project from qtDesigner documentation, I am greeted with this,

> 
conversionform.h:16:24: error: Q3VBoxLayout: No such file or directory
conversionform.h:17:24: error: Q3GridLayout: No such file or directory
conversionform.h:18:24: error: Q3HBoxLayout: No such file or directory
conversionform.h:19:18: error: QLabel: No such file or director


After modifying the make file to point at the qt3 by adding -I/usr/include/qt4/Qt3Support/, the compiler finds the above files but then I recieve MANY other compiler errors.

> g++ -c -pipe -Wall -W -O2 -D_REENTRANT -DQT_NO_DEBUG -DQT_THREAD_SUPPORT  -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -I/usr/include/qt4/Qt3Support/ -o main.o main.cpp
In file included from /usr/include/qt4/Qt3Support/Q3VBoxLayout:1,
                 from conversionform.h:16,
                 from main.cpp:2:
/usr/include/qt4/Qt3Support/q3boxlayout.h:27:30: error: QtGui/qboxlayout.h: No such file or directory
In file included from main.cpp:2:
conversionform.h:19:18: error: QLabel: No such file or directory
/usr/include/qt4/Qt3Support/q3boxlayout.h:29: error: ‘QT_BEGIN_HEADER’ does not name a type
/usr/include/qt4/Qt3Support/q3boxlayout.h:55: error: expected class-name before ‘{’ token
/usr/include/qt4/Qt3Support/q3boxlayout.h:73: error: ISO C++ forbids declaration of ‘Q3HBoxLayout’ with no type
/usr/include/qt4/Qt3Support/q3boxlayout.h:74: error: expected ‘;’ before ‘}’ token
/usr/include/qt4/Qt3Support/q3boxlayout.h:74: error: expected `;' before ‘}’ token
/usr/include/qt4/Qt3Support/q3boxlayout.h: In constructor ‘Q3HBoxLayout::Q3HBoxLayout()’:
/usr/include/qt4/Qt3Support/q3boxlayout.h:57: error: class ‘Q3HBoxLayout’ does not have any field named ‘Q3BoxLayout’
/usr/include/qt4/Qt3Support/q3boxlayout.h:57: error: ‘LeftToRight’ was not declared in this scope
/usr/include/qt4/Qt3Support/q3boxlayout.h: In constructor ‘Q3HBoxLayout::Q3HBoxLayout(QWidget*)’:
... Many more ....


Is there a simple howto anywhere as following the instructions on the trolltech site don't seem to help. 

This is on Edgy amd64, if its any help.

---

### Post by abickerton on 2007-06-16
So much for the 'legendary' community support, this is a few months old and I'm still non the wiser.

---

### Post by Hendrixski on 2007-08-01
Yeah, for real.  I have a question about setting variables for a qt project as well... and google was all over the map on it, so I figure I have to come here and post.  But like all good posters I searched the forums before posting in case it was already answered.

---

