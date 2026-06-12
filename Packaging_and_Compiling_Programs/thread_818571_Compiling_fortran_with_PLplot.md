---
title: "Compiling fortran with PLplot"
date: 2008-06-04
forum: Packaging and Compiling Programs
---

### Post by dre222 on 2008-06-04
Hello,

PLplot was installed on our network, and I am trying to compile a fortran program that uses it.  There are many examples on the website about how to use the package, but nothing about compiling ([http://plplot.sourceforge.net/index.html](http://plplot.sourceforge.net/index.html)). 

I have many compilers (g77, f90, xls ...),which I tried while liking the file to the library, even thought I'm not sure where the library is. I've done some locating and I've come about some folders in the /usr/lib/ directory (UNIX/LINUX system), that could be the correct lickable librairies, but I have no idea which ones I should link.

What I'd like to learn is what command to give in this sort of situation. The main structure I've been using : 
COMPILER filename.f -ld LIBRARY_DIR -o filename.e

And I also have to say that I've been mixing and matching different compilers with some library folders.

I've also tried the "using" command directly in the code file.

thx

---

