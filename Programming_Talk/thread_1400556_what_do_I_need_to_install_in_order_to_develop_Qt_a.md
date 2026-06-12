---
title: "what do I need to install in order to develop Qt applications?"
date: 2010-02-07
forum: Programming Talk
---

### Post by guest_user on 2010-02-07
using kubuntu, what packages do I need?

---

### Post by Zorgoth on 2010-02-07
Personally, I just install Qt Designer for the dependencies even though I don't use it much because I'm kind of lazy.

In theory I think you need to install the packages starting with 
"libqt4-," in particular the basic libraries are, I think:

Qtcore

QtGui.

QtSql,

QtOpenGL

QtXml

Qt3supprt

QtSvg

QtAssistantClient

QTestLib

QtDBus

I just edit them in a text file but you can use Qt Designer I assume which is also in the repository.

DISCLAIMER:  I am a noob.

EDIT: QT designer not developer

---

### Post by Reiger on 2010-02-07
Those are libraries, but in order to build the software you want to develop you may either need a bindings library (such as PyQt) or you may need the headers (-dev packages).

---

### Post by Zorgoth on 2010-02-07
Probably also need qt4-qmake

---

### Post by guest_user on 2010-02-07
I've installed libqt4-dev and qt designer but I still get the QApplication: No such file or directory error, what should I do?
ok nvm, I used qmake and it worked fine, but is there any way I can compile it normally using g++ without using qmake?

---

### Post by Zorgoth on 2010-02-08
I am 99.9% sure that qmake is 100% necessary.

---

### Post by Zugzwang on 2010-02-08
> **Zorgoth said:**
> I am 99.9% sure that qmake is 100% necessary.

Here's the missing 0.1% - There's also the possibility to use "cmake" instead of "qmake".

Also, qmake isn't absolutely necessary, but there are some additional steps involved in compiling which you will need to mimic (unless you are only doing trivial stuff with Qt). When invoking "make" after a "make clean" on your project that compiles with qmake, have a look at the commands that "make" invokes in order to build your application. Of course you can always do this by hand, but it's cumbersome.

---

