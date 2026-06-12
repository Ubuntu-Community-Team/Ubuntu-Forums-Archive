---
title: "Ugh. I can't get my first Qt app to compile"
date: 2009-07-13
forum: Programming Talk
---

### Post by Pogeymanz on 2009-07-13
I'm doing the standard hello-world app from TrollTech's Qt programming guide.
```
#include <QApplication>
#include <QLabel>

int main(int argc, char *argv[])
{
  QApplication app(argc, argv);
  QLabel *label = new QLabel("Hello Qt!");
  label->show();
  return app.exec();
}

```

then I run 
```
qmake-qt4 -project
qmake-qt4
make
```

and gcc returns this
```
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o hello.o hello.cpp
hello.cpp:1:24: error: QApplication: No such file or directory
hello.cpp:2:18: error: QLabel: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:6: error: ‘QApplication’ was not declared in this scope
hello.cpp:6: error: expected `;' before ‘app’
hello.cpp:7: error: ‘QLabel’ was not declared in this scope
hello.cpp:7: error: ‘label’ was not declared in this scope
hello.cpp:7: error: expected type-specifier before ‘QLabel’
hello.cpp:7: error: expected `;' before ‘QLabel’
hello.cpp:9: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:4: warning: unused parameter ‘argc’
hello.cpp:4: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

```

I've googled and this seems to be a common beginning speed bump, but none of the solutions I found work for me.

Here are the qt packages I have installed
```
dpkg --get-selections | grep qt
libavahi-qt3-1					install
libdbus-qt-1-1c2				install
libqt3-mt					install
libqt4-assistant				install
libqt4-dbus					install
libqt4-designer					install
libqt4-help					install
libqt4-network					install
libqt4-opengl					install
libqt4-qt3support				install
libqt4-script					install
libqt4-scripttools				install
libqt4-sql					install
libqt4-sql-mysql				install
libqt4-sql-sqlite				install
libqt4-svg					install
libqt4-test					install
libqt4-webkit					install
libqt4-xml					install
libqt4-xmlpatterns				install
libqtcore4					install
libqtgui4					install
qt3-qtconfig					install
qt4-demos					install
qt4-designer					install
qt4-dev-tools					install
qt4-doc						install
qt4-qmake					install
qt4-qtconfig					install

```

---

### Post by dwhitney67 on 2009-07-13
It looks like you are missing the libqt4-dev (and possibly libqt4-opengl-dev) packages.

---

### Post by Pogeymanz on 2009-07-13
Ah, that was it!

I can't tell you how long I was staring at synaptic and didn't even see that package.

Now my problem is that synaptic wont let me install it because it depends on some Xorg libraries whose versions don't match mine since I installed a newer version of xorg... ugh

EDIT: All done downgrading and now everything is golden. Thanks.

---

### Post by abhilashm86 on 2009-07-14
hi, will it be better if you download whole Qt 4.5 SDK package from trolltech.com and install, then you don't need to bother much about compilation and debugging stuff, qt will take care of it.

---

### Post by Zugzwang on 2009-07-14
> **abhilashm86 said:**
> hi, will it be better if you download whole Qt 4.5 SDK package from trolltech.com and install, then you don't need to bother much about compilation and debugging stuff, qt will take care of it.

Why should that be the case? You still have to give the include paths and so on, except if you use "qmake" - which the OP is already doing. And what does this have to do with debugging? Once the executable has been built, it should be the same.

---

### Post by JordyD on 2009-07-14
> **abhilashm86 said:**
> hi, will it be better if you download whole Qt 4.5 SDK package from trolltech.com and install, then you don't need to bother much about compilation and debugging stuff, qt will take care of it.

I think it's better to use your package manager whenever possible. It keeps things nice and clean. Plus, when you're looking for libraries, if you just remember to install the *-dev packages, you'll be fine, as those install other things as dependencies and all is good.

---

