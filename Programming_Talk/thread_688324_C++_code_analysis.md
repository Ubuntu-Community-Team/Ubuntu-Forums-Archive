---
title: "C++ code analysis"
date: 2008-02-05
forum: Programming Talk
---

### Post by jasonlfunk on 2008-02-05
I inherited 30  thousand lines of poorly commented/documented cpp code from an ongoing project that I need to figure out how it works. Does anyone know of some software that I can use to analyze it and find function maps (what functions call what), variable usage, stuff like that?

---

### Post by Zugzwang on 2008-02-05
You can try to use doxygen to generate some documentation like calling graphs (as far as I know).

Some UML tools like "Borland Together" (warning: commercial!) also generate nice graphs out of existing codes. There may be free alternatives but I don't know.

Finally, don't forget that you can still debug the code and ask the writer if you have any specific problems/questions. If he/she used design patterns heavily, you might want to look into tutorials on that or buy/lend a suitable book.

---

### Post by aks44 on 2008-02-05
I second Zugzwang's suggestion, doxygen + graphviz will generate a nice API reference, including dependency graphs (at the function/class level as well as at the file level) and many other goodies. The HTML output is particularly nice for exploring unknown code bases.

> **Zugzwang said:**
> Some UML tools like "Borland Together" [...] There may be free alternatives but I don't know.
FYI, doxygen is indeed the free alternative you're evoking. I have no experience with the specific product "Borland Together" but I doubt that it provides much more functionality than doxygen (which is quite a complete product).

---

### Post by jasonlfunk on 2008-02-05
Thanks a lot. I'll give it a shot

---

### Post by Cypher on 2008-02-05
If it was C code, I would've suggested CScope which will parse all files and allow you to figure where functions are defined and which function is calling which function and all that.

CScope will work with C++, but just not as well as C code, but you can use it to quickly search for functions, variable in C++ code.

---

### Post by speedbaron on 2012-04-11
There is also a good commercial product called Understand C from Scitools; [http://www.scitools.com/](http://www.scitools.com/)

---

### Post by fct on 2012-04-11
You might also enjoy cppcheck, a static analysis tool to find potential bugs in code:

[http://cppcheck.sourceforge.net/](http://cppcheck.sourceforge.net/)

---

### Post by 3Miro on 2012-04-11
Code::Blocks has some nice features like "where is this function called", but it may be too basic for you.

---

### Post by muteXe on 2012-04-12
i've not tried this on a linux box but if you want some class diagrams built you could try and install the free trial version of Enterprise Architect and reverse engineer the code.

---

