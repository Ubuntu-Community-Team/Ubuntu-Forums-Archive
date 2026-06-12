---
title: "Easy compiling under C++ - autocompile?"
date: 2008-03-07
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-03-07
Does anyone know of a C++ compiler that is as easy to use as the Java or .NET compiler?  Meaning that you don't create a makefile, but instead just call the files and list the files that should be included?  Visual Studio VCProj is about half of the way there, but still too complex.

---

### Post by S15_88 on 2008-03-07
you can use a simple text editor for your code then compile in the terminal with gcc.
or you can try an IDE like anjuta.

Thanks, ALain

---

### Post by SNYP40A1 on 2008-03-07
I am compiling multiple files including another software package.

---

### Post by S15_88 on 2008-03-07
not sure what the flag for g++ is but in gcc just use -c to compile multiple files.
i do
gcc -c main.c -o main.o
gcc -c somefunc.c -o somefunc.o

gcc main.o somefunc.o -o executable

./executable

hope that helps!

Thanks, ALain

---

