---
title: "singlr rooted hierarchy in oop....."
date: 2009-08-03
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-03
i read that to maintain backward compatibility, we need to use single rooted system, having only one main base class, and deriving from it.....
what are other advantages of doing like this? i've not expreinced or worked on these concepts, still learning.........
which is better to design and implement in oop, single rooted hierachy or many base classes in c++ and java?

---

### Post by nvteighen on 2009-08-03
Well, an advantage I see is it allows you to have methods valid for all your classes... Common Lisp does this by default, by having everything derived from T ("True") and all primitives are also derived from T... except nil (which is "False" :))

---

### Post by Habbit on 2009-08-03
Well, Java _forces_ you to use single inheritance, at least of classes with code: you can inherit from several _interfaces_, but only one base class. C++, however, allows multiple inheritance, but it should be handled with care, as it can lead to complex inheritance relationships.

---

