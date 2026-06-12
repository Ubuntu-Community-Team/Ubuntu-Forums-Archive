---
title: "compiling hello.c"
date: 2009-09-09
forum: Packaging and Compiling Programs
---

### Post by joshua1983 on 2009-09-09
Hi, I'm trying to compile hello.c from apt-get sources hello but I get this error...

```

hello.c:20:20: error: config.h: No existe el fichero ó directorio
En el fichero incluído de hello.c:21:
system.h:33:21: error: gettext.h: No existe el fichero ó directorio
system.h:38:22: error: closeout.h: No existe el fichero ó directorio

```

It Say's can't found gettext.h and closeout.h library, even I have installed libc6 and libc6-dev.

Thanks in advance

---

### Post by mc4man on 2009-09-10
Why don't you post your complete terminal including prompt and command

If you're doing what I think those 2 files are in the source

( they are gnulibs, but you shouldn't need the gnulib package installed to do what you're doing

---

### Post by joshua1983 on 2009-09-10
there is all output, even some ls... 

```


joshua@joshua-desktop:~/Documentos/code_dev/hello/hello-2.2$ ls
ABOUT-NLS   AUTHORS    ChangeLog    config.in  configure.ac  COPYING  gnulib   Makefile.am  man   po      src    THANKS
aclocal.m4  build-aux  ChangeLog.O  configure  contrib       debian   INSTALL  Makefile.in  NEWS  README  tests  TODO
joshua@joshua-desktop:~/Documentos/code_dev/hello/hello-2.2$ cd src/
joshua@joshua-desktop:~/Documentos/code_dev/hello/hello-2.2/src$ ls
ChangeLog  hello.c  Makefile.am  Makefile.in  system.h
joshua@joshua-desktop:~/Documentos/code_dev/hello/hello-2.2/src$ gcc hello hello.c 
gcc: hello: No existe el fichero ó directorio
hello.c:20:20: error: config.h: No existe el fichero ó directorio
En el fichero incluído de hello.c:21:
system.h:33:21: error: gettext.h: No existe el fichero ó directorio
system.h:38:22: error: closeout.h: No existe el fichero ó directorio
hello.c: En la función ‘main’:
hello.c:62: error: ‘close_stdout’ no se declaró aquí (primer uso en esta función)
hello.c:62: error: (Cada identificador no declarado solamente se reporta una vez
hello.c:62: error: para cada funcion en la que aparece.)
hello.c:95: aviso: declaración implícita incompatible de la función interna ‘gettext’
hello.c:104: aviso: declaración implícita incompatible de la función interna ‘gettext’
hello.c: En la función ‘print_help’:
hello.c:140: aviso: declaración implícita incompatible de la función interna ‘gettext’
hello.c:170: error: ‘PACKAGE_BUGREPORT’ no se declaró aquí (primer uso en esta función)
hello.c: En la función ‘print_version’:
hello.c:180: error: ‘PACKAGE’ no se declaró aquí (primer uso en esta función)
hello.c:180: error: ‘VERSION’ no se declaró aquí (primer uso en esta función)
hello.c:187: aviso: declaración implícita incompatible de la función interna ‘gettext’



```

I've already installed gnulib... so I want to know how to specify missing libraries...
Thanks for all

---

### Post by MadCow108 on 2009-09-10
you need to run ./configure which creates the Makefile
and the run: make
this compiles it
and "make install" installs it
more information is in the INSTALL file

for more information on autotools (the tools used to create these scripts):
[http://sourceware.org/autobook/autobook/autobook_toc.html](http://sourceware.org/autobook/autobook/autobook_toc.html)

---

### Post by joshua1983 on 2009-09-10
wow.... yes It's too easy... thanks for the answer...

---

