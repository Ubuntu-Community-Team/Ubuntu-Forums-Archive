---
title: "Gedit question with headers"
date: 2007-11-09
forum: Programming Talk
---

### Post by sdmike on 2007-11-09
How do I link header files using Gedit?

So if I have my main C++ file like work.cpp and I'm linking a function in function.h to it.

---

### Post by samjh on 2007-11-09
Gedit is just a text editor, not an IDE.

It does not do any automatic linking of header files, or any sort of project management or automated builds.

If you want to link your program to custom libraries or headers, then you'll need to use appropriate g++ linker flags (the -I, -l and -L flags, in particular).  Take a look at the g++ and gcc man pages.
```
man g++
```

In summary, you need to use the -I flag to specify where your function.h file is, the -L flag to specify where the library file is located, and -l to specify which library to link to.

Example:
```
g++ -o work work.cpp -I/home/project/function.h -L/home/project/libs -lfunction
```

---

