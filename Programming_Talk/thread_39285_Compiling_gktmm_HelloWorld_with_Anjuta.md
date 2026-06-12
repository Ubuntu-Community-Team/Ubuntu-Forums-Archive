---
title: "Compiling gktmm HelloWorld with Anjuta"
date: 2005-06-04
forum: Programming Talk
---

### Post by std on 2005-06-04
Hello,
I've searched around the forums a bit but found no trace of what I'm trying to solve. Google wasn't too helpful either.
I'm trying to compile the simple Hello, World! program that can also be found in gtkmm's documentation over here: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s06.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s06.html) . While everything seems to work fine (no parsing errors, the code is free of any syntax errors), I end up with the following error message:

```
undefined reference to: 'HelloWorld::HelloWorld[in-charge]()'
``` 

There are two errors identical to the one above, except for the fact that the undefined reference is to HelloWorld::~HelloWorld[in-charge]() (the destructor of the HelloWorld class and not the constructor).

Later edit: I forgot to mention something that may be important. I'm using Anjuta 1.2.2 and GTKmm version 2.0, the one found in the Ubuntu 5.04 repositories.

Has anyone encountered such a problem, or at least happens to have a clue about how I could solve it?
A small explanation about what the [in-charge] means would also be helpful to me, I'm well on my way on OOP and I would appreciate any kind of help.

Thank you in advance.

---

