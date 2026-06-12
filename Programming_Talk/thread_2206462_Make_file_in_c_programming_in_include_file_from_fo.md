---
title: "Make file in c programming in include file from folder"
date: 2014-02-19
forum: Programming Talk
---

### Post by Ravi_Chander_Jha on 2014-02-19
Hello everyone, i am facing some trouble while including header and source file into my c codes.
The include directory structure is illustrated on [http://csapp.cs.cmu.edu/public/code.html](http://csapp.cs.cmu.edu/public/code.html)
My code resides in code/mycodes so please let me know the structure of makefile for codes in mycodes

---

### Post by dargaud2 on 2014-02-19
That's a whole bunch of different programs. Aren't makefiles provided ? If not you can compile simple programs with "gcc -o hello.exe hello.c". For anything more complex, checkout some simple makefile tutorials, there are plenty on google.

---

### Post by kangaba on 2014-02-19
Take the time to learn a build system, be it Gnu Autotools or CMake (the latter is easier and more modern). It's hard, takes weeks or months, but you can't endlessly rely on copy-pasting random help solutions from the internet.

---

