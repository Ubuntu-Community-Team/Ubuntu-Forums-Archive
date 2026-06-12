---
title: "Can't find libxml/parser.h"
date: 2010-01-30
forum: Programming Talk
---

### Post by Bucephalus01 on 2010-01-30
Hi

I'm doing the anjuta tutorial on the anjuta homepage, specifically up to this page: 
[http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-autotools.html.en](http://library.gnome.org/users/anjuta-build-tutorial/2.26/library-autotools.html.en)


And well, I get this error following. I have double checked all steps on this page, and even cut and pasted the code into my version of main.c, but still the error rises. Also, I did a find / -name "parser.h" and the file and libxml are definitely there in usr/include/libxml2/libxml/parser.h

Here is the error:

david@Alexander:~/projects/learninganjuta/tutorials/tut_prog$ make
gcc -DPACKAGE_NAME=\"Tutorial\ Program\" -DPACKAGE_TARNAME=\"tutorial-program\" -DPACKAGE_VERSION=\"1.0\" -DPACKAGE_STRING=\"Tutorial\ Program\ 1.0\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"tutorial-program\" -DVERSION=\"1.0\" -I.     -g -O2 -MT tut_prog-main.o -MD -MP -MF .deps/tut_prog-main.Tpo -c -o tut_prog-main.o `test -f 'main.c' || echo './'`main.c
main.c:1:30: error: libxml/parser.h: No such file or directory
main.c: In function ‘main’:
main.c:6: error: ‘xmlDocPtr’ undeclared (first use in this function)
main.c:6: error: (Each undeclared identifier is reported only once
main.c:6: error: for each function it appears in.)
main.c:6: error: expected ‘;’ before ‘doc’
main.c:7: error: ‘doc’ undeclared (first use in this function)
make: *** [tut_prog-main.o] Error 1


I'm particularly worried about the line where it says error: "libxml/parser.h: No such file or directory"

I could find it, but for some reason this program couldn't

Please help if you know what I'm doing wrong or what is happening.

---

### Post by dwhitney67 on 2010-01-30
You need to tell Anjuta where to find the libxml header files, since after all, they are not directly stored within /usr/include.

Thus what you ultimately need is for the gcc statement to also include a -I/usr/include/libxml2 directive.

The -I (uppercase 'eye') instructs gcc where to find header files that are in non-standard areas.  The subdirectory libxml2 is such a candidate.

---

### Post by MadCow108 on 2010-01-30
you probably have to regenerate your project:
build->configure program: mark regenerate
this rerun all the autotool stuff, although it says in the tutorial that it should work automatically I found it necessary sometimes (and the documentation quality of anjuta is not very good)


also check on command line if pkg-config knows about the package in question

---

### Post by Bucephalus01 on 2010-01-30
yeah I actually did check pkg-config and it knows about it.
Well, I'm doing the part in the tutorial where it shows you how do create a project without Anjuta, so really Anjuta doesn't come into it at this stage of the tutorial. It's all using autotools in the raw fashion.

Let me invistigate what you have said a little more.

thanks.

---

### Post by Bucephalus01 on 2010-01-30
Sorry this part of the tutorial is on adding a new library, not making a new project.

---

### Post by Bucephalus01 on 2010-01-30
Yeah I'm looking at the print out of what they expect from the make command, and it's not the same as what I have. And mine is deficient of the -I/usr/include/libxml2 directive you mentioned, while the tutorial has that. 

let me look more.

---

### Post by Bucephalus01 on 2010-01-30
Later in the tutorial it says another way to do it, and it's virtually what you said dwhitney67. So I went on ahead and put it in the makefile directly and it worked. For some reason that configure.ac file is either not creating the variable I was using in the Makefile.am, or it wasn't putting the right value in that variable, or the Makefile.am wasn't picking up the variable.

Either way, I'm not going to invest more time in this as to why since I have found a solution that works.

Thanks for your help both of you.

---

### Post by metalheart on 2010-03-06
Had same error and apparently all macros have to be put after AC_INIT and before AC_OUTPUT macros like this:

```

AC_INIT([Tutorial Program], 1.0)
...
PKG_CHECK_MODULES(XML, libxml-2.0 >= 2.4)
...
AC_OUTPUT

```

HTH

---

