---
title: "qt4 compilation issue"
date: 2007-05-12
forum: Programming Talk
---

### Post by prophet001 on 2007-05-12
Hey guys (and girls, one would hope), I'm having trouble compiling qt4 in feisty fawn. When I try to run make, I get this error:

make[3]: *** [.obj/debug-shared/qapplication.o] Error 1
make[3]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src/gui'
make[2]: *** [debug-all] Error 2
make[2]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src/gui'
make[1]: *** [sub-gui-make_default-ordered] Error 2
make[1]: Leaving directory `/home/ben/qt-x11-opensource-src-4.0.1/src'
make: *** [sub-src-make_default-ordered] Error 2


I honestly have no clue what this refers to, and I wasn't sure I had posted it in the right place, but any help would be great!

---

### Post by seamless on 2007-05-13
That really doesn't say a whole lot, the actual error should be more above those messages.

Also unless you are planning on developing with one of the beta releases, 4.2 is available in the repositories and can be installed along side 3.x.

---

