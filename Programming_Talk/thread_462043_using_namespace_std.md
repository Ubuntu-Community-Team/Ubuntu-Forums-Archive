---
title: "using namespace std"
date: 2007-06-02
forum: Programming Talk
---

### Post by bluewagon on 2007-06-02
how big of a thing is this? is this something that i should really learn because in my c++ program class we never used it and always did iostream.h but everytime i look online for help they always do iostream, using namespace std
and some IDES like devcpp wouldnt let me use iostream.h

---

### Post by Zdravko on 2007-06-02
std is the standard namespace in C++, that is every C++ function, class, type or variable is defined in it. You can explicitly write std:: in front of each call to such function or class, or act lazy by writing "using namespace std;" somewhere in the beginning of the cpp file. The choice is yours.
Btw, iostream.h is considered deprecated. Versions without ".h" postfix are better.

---

