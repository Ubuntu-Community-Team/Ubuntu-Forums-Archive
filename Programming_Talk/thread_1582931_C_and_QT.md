---
title: "C and QT"
date: 2010-09-27
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-09-27
I wrote a C application , now  want to make a GUI for this application, can I use QT ?  [http://qt.nokia.com/]("http://qt.nokia.com/")
I know about gtk but I'm assuming QT is easier and maybe more powerful ?

---

### Post by dwhitney67 on 2010-09-27
IIRC, Qt is based on C++.

So the question you should be asking is whether you can use C from within a C++ application?  And the answer is "yes".

---

### Post by cap10Ibraim on 2010-09-27
ok , thanks , next i'll be downloading the complete SDK 500 MB  !

---

### Post by nvteighen on 2010-09-27
Qt is a C++ library. AFAIK, you can't use a C++ library in a C program (you can use a C library in a C++ program, though). Either code in C++ or use GTK+, which is a C library.

GTK+ and Qt are pretty much the same. Ok, Qt also has a lot of stuff not related to GUIs, but networking and other stuff but that's because Qt predates the C++ standard... Save for that, they are equally powerful and it's more a matter of taste (or platform-targetting) whether you use any of both.

---

### Post by schauerlich on 2010-09-27
> **nvteighen said:**
> Qt is a C++ library. AFAIK, you can't use a C++ library in a C program (you can use a C library in a C++ program, though). Either code in C++ or use GTK+, which is a C library.

GTK+ and Qt are pretty much the same. Ok, Qt also has a lot of stuff not related to GUIs, but networking and other stuff but that's because Qt predates the C++ standard... Save for that, they are equally powerful and it's more a matter of taste (or platform-targetting) whether you use any of both.

Well, if you write C code but compile with g++ it should work, as long as you avoid some [incompatibilities](http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B).

---

### Post by cap10Ibraim on 2010-09-27
Yes I already use g++ for compilation , 
but that's what make me consider Qt [http://qt.nokia.com/qt-in-use]("http://qt.nokia.com/qt-in-use")
I've got his book The.Book.of.Qt.4.The.Art.of.Building.Qt.Applications(pirated...I Know..)
any other recommendations to get me started

---

