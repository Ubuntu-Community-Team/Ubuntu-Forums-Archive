---
title: "funny c++ bug (?)"
date: 2006-01-10
forum: Programming Talk
---

### Post by kornelix on 2006-01-10
I made the following syntax coding error:
   char *buff = new char(500);     //  instead of [500]

The compiler accepted this. The program crashed after reading something into the above buffer. You can imagine how interesting (painful) the debugging was.

Question: is the compiler nuts or is this syntax legitimate for something I do not understand?
I am using the default g++ compiler.

---

### Post by LordHunter317 on 2006-01-10
[QUOTE=kornelix]Question: is the compiler nuts or is this syntax legitimate for something I do not understand?[/quote]It is.  You're allocating space for a *single* char on the freestore, and giving it the value 500.

C++ allows you to declare and initalize primitive types just like you would for classes:```
int foo(10);
long bar(12345);
```

If you want an array, you must use the array new (new []) syntax.

---

