---
title: "Undefined reference problem with g++ and Qt3"
date: 2008-11-22
forum: Programming Talk
---

### Post by adrianmcknight on 2008-11-22
I have been running into a problem compiling using Qt3. I just started learning qt so I'm a bit at a loss.

I made a simple test case to demonstrate the problem.

```

  1 #include <qapplication.h>
  2
  3 int main(int argc, char* argv[]){
  4    QApplication a(argc, argv);
  5 }

```

So when I try to compile this, I get the following error.

The command I use is :
    g++ -I /usr/include/qt3 simple.cpp

```


/tmp/ccioDLHI.o: In function `main':
simple.cpp:(.text+0x12f): undefined reference to `QApplication::QApplication(int&, char**)'
simple.cpp:(.text+0x13a): undefined reference to `QApplication::~QApplication()'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0xc): undefined reference to `QGList::clear()'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x10): undefined reference to `QGList::~QGList()'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x14): undefined reference to `QGList::~QGList()'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x18): undefined reference to `QPtrCollection::newItem(void*)'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x20): undefined reference to `QGList::compareItems(void*, void*)'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x24): undefined reference to `QGList::read(QDataStream&, void*&)'
/tmp/ccioDLHI.o:(.rodata._ZTV6QGList[vtable for QGList]+0x28): undefined reference to `QGList::write(QDataStream&, void*) const'
/tmp/ccioDLHI.o:(.rodata._ZTI6QGList[typeinfo for QGList]+0x8): undefined reference to `typeinfo for QPtrCollection'
collect2: ld returned 1 exit status

```

So... any ideas?

---

### Post by snova on 2008-11-22
You didn't link with the library. I'm not sure what the filename is (I'm only familiar with Qt4), but adding -lqt-mt to the command line *might* do it.

---

### Post by dexter on 2008-11-22
I'm not sure about qt3 but when i experimented with qt4, I used qmake to generate makefiles, so all includes and libraries were automatically set properly. Perhaps this is also used with qt3?

---

### Post by snova on 2008-11-22
Yes, there is a QMake for Qt3, in the qt3-dev-tools, which will ease your life considerably.

---

### Post by adrianmcknight on 2008-11-22
the -lqt-mt did the trick, thanks.

I'll look into qmake

---

