---
title: "C++ Compiler?"
date: 2010-04-15
forum: Programming Talk
---

### Post by asddf on 2010-04-15
I'm currently doing C++ on windows in Visual Studio, but could someone recommend a good Linux compiler?

---

### Post by Mordred on 2010-04-15
Hi,

gcc (g++) should do the compiling trick.

You typically would want to install build-essential since 
this includes some other stuff you will need.

[PHP]$sudo apt-get build-essential[/PHP]

If you also need an IDE you could have a look at elipse, code::blocks, ... 
Have a look in one of the many 'which IDE should I use' threads 
here on the forum.

---

### Post by UBJim on 2010-04-15
Also install Eclipse CDT after the build tools.
eclipse-cpp-galileo-SR2-linux-gtk.tar.gz
 -  You will also need to install the Java runtime.

This will give an set up where you can compile and run in a gui.

---

### Post by Linuxforall on 2010-04-15
Anjuta, Eclipse.

---

### Post by azagaros on 2010-04-15
gcc would be the compiler suite on linux distributions.

I personally would recommend Codelite for the IDE.  Netbeans and Eclipse may need more to set up.

---

### Post by History500 on 2010-04-15
gcc /path/to/file.cpp

Should work.

But you can also get GUI based compilers if you want more in-depth IDE like interfaces and what not.

---

### Post by CptPicard on 2010-04-15
It won't work. "g++" is the C++ compiler. "gcc" is the C compiler. GCC is the name of the collection of compilers.

---

