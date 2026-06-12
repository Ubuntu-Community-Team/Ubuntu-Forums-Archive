---
title: "AVL Tree operator= and copy constructor"
date: 2012-11-10
forum: Programming Talk
---

### Post by dempa on 2012-11-10
I have a header file avl_tree.h [http://pastie.org/private/sjnht28clk5q5zkfx8okw](http://pastie.org/private/sjnht28clk5q5zkfx8okw)
and test program [http://pastie.org/private/xlintocl6ozdme2n6bl3wa](http://pastie.org/private/xlintocl6ozdme2n6bl3wa).

I'm afraid my copy constructor and operator= are not working properly as they do not print when the printTree() function is called on them. I know that the copyNodes() is working properly because the cout on line 242 reflects that t->element and r->element are the same. Why do lines 31 and 35 of the test program produce no output?

Any help on this would be much appreciated.

---

### Post by dempa on 2012-11-10
[http://pastie.org/private/7alvdpiorvbmazjmpj8kua](http://pastie.org/private/7alvdpiorvbmazjmpj8kua)
[http://pastie.org/private/6evgmigui3exg4f9orawcw](http://pastie.org/private/6evgmigui3exg4f9orawcw)

Here are simpler versions of the code. I left printTree out because I know it works correctly.

---

### Post by ofnuts on 2012-11-10
> **dempa said:**
> [http://pastie.org/private/7alvdpiorvbmazjmpj8kua](http://pastie.org/private/7alvdpiorvbmazjmpj8kua)
[http://pastie.org/private/6evgmigui3exg4f9orawcw](http://pastie.org/private/6evgmigui3exg4f9orawcw)

Here are simpler versions of the code. I left printTree out because I know it works correctly.
Do you get the expected output size from copyNodes() (one line per element copied)?

---

### Post by dempa on 2012-11-10
I figure it out. I needed to pass a reference of a pointer to copyNodes().

---

