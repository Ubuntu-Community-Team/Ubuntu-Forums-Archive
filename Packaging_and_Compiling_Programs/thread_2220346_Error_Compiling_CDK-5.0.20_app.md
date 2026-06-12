---
title: "Error Compiling CDK-5.0.20 app"
date: 2014-04-27
forum: Packaging and Compiling Programs
---

### Post by Kaizzer on 2014-04-27
Hello

I am devoloping a simple app using code from the CDK-5.0.20 ncurses package. For that i've modified one of the examples and made it work just fine (really simple one actually).   ==> **Inicio.c**

Then ive tryed to make my first library **(Tools.c)**  with some usefull tools (logging, text/date formating code) that i intend to use crosswide my future development. 

I modified the MakeFile in to include this library but it raises an error that i cant deal with .. (i dont know how) 

Here is the Makefile that i have. 
```

# $Id: Makefile.in,v 1.21 2013/07/19 23:55:03 tom Exp $
  2 #
  3 # Makefile for the examples directory.
  4 #
  5 SHELL           = /bin/sh
  6 
  7 prefix          = /usr/local
  8 exec_prefix     = ${prefix}
  9 
 10 srcdir          = .
 11 
 12 
 13 CC              = gcc
 14 RM              = rm -f
 15 CTAGS           =
 16 ETAGS           =
 17 LINT            =
 18 LINT_OPTS       =
 19 
 20 LIBS            = -lcdk -lncurses
 21 
 22 LIBTOOL         =
 23 LIBTOOL_CLEAN   =
 24 LIBTOOL_LINK    = ${CC}
 25 LINK            = $(LIBTOOL_LINK)
 26 
 27 x               =
 28 o               = .o
 29 LOCAL_LIBDIR    = .
 30 
 31 CFLAGS          = -g -O2
 32 CPPFLAGS        = -DHAVE_CONFIG_H -I../include -I$(srcdir)/../include -I.  -D_GNU_SOURCE
 33 LDFLAGS         = -L.. -L/lib
 34 #
 35 #Agregar Nuevas piezas acá 
 36 #
 37 BINS    = \
 38         Tools$x\
 39         Inicio$x
 40 CKDKSRC = \
 41         Tools.c\
 42         Inicio.c
 43 
 44 LINKIT  = $(LINK) $(CFLAGS) $(CPPFLAGS) $? -o $@ $(LDFLAGS) $(LIBS)
 45 
 46 all : $(BINS)
 47 #
 48 #Agregar Nuevas piezas TAMBIEN acá 
 49 #
 50 
 51 Tools$x :               Tools.c         ; $(LINKIT)
 52 Inicio$x :              Inicio.c                ; $(LINKIT)
 53 #
 54 # Standard clean directives.
 55 #
 56 clean::
 57         -$(LIBTOOL_CLEAN) $(RM) *.o core $(BINS)
 58 
 59 distclean:: clean
 60         $(RM) Makefile
 61 
 62 #tags :
 63 #       $(CTAGS) *.[ch] */*.[ch]
 64 
 65 #TAGS :
 66 #       $(ETAGS) *.[ch] */*.[ch]
 67 
 68 lint: $(CDKSRC)
 69         $(LINT) $(LINT_OPTS) $(CPPFLAGS) $(CDKSRC)

```

and im getting this error when compiling 

```

kiltran@Olympus:~/MyDev/ncurses/cdk-5.0-20140118/DocTec$ make -f MakeDocTec 
gcc -g -O2  -DHAVE_CONFIG_H -I../include -I./../include -I.  -D_GNU_SOURCE Tools.c -o Tools -L.. -L/lib   -lcdk -lncurses 
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 0 tiene un índice de símbolo 11 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 1 tiene un índice de símbolo 12 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 2 tiene un índice de símbolo 2 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 3 tiene un índice de símbolo 2 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 4 tiene un índice de símbolo 11 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 5 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 6 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 7 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 8 tiene un índice de símbolo 12 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 9 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 10 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 11 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 12 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 13 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 14 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 15 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 16 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 17 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 18 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 19 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 20 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 21 tiene un índice de símbolo 22 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_line): la reubicación 0 tiene un índice de símbolo 2 inválido
/usr/lib/gcc/i686-linux-gnu/4.8/../../../i386-linux-gnu/crt1.o: En la función `_start':
(.text+0x18): referencia a `main' sin definir
collect2: error: ld returned 1 exit status
make: *** [Tools] Error 1



```

As you can see at the bottom, it sais main has no defined refferene .. but Tools.c has no main since is just a compilation of usefullo functions. 

Any ideas and tips would be much appreciated! 
Thanks in advace !
Regards. from Chile :D

---

### Post by Carlos_Enrique on 2014-10-03
> **Kaizzer said:**
> Hello

I am devoloping a simple app using code from the CDK-5.0.20 ncurses package. For that i've modified one of the examples and made it work just fine (really simple one actually).   ==> **Inicio.c**

Then ive tryed to make my first library **(Tools.c)**  with some usefull tools (logging, text/date formating code) that i intend to use crosswide my future development. 

I modified the MakeFile in to include this library but it raises an error that i cant deal with .. (i dont know how) 

Here is the Makefile that i have. 
```

# $Id: Makefile.in,v 1.21 2013/07/19 23:55:03 tom Exp $
  2 #
  3 # Makefile for the examples directory.
  4 #
  5 SHELL           = /bin/sh
  6 
  7 prefix          = /usr/local
  8 exec_prefix     = ${prefix}
  9 
 10 srcdir          = .
 11 
 12 
 13 CC              = gcc
 14 RM              = rm -f
 15 CTAGS           =
 16 ETAGS           =
 17 LINT            =
 18 LINT_OPTS       =
 19 
 20 LIBS            = -lcdk -lncurses
 21 
 22 LIBTOOL         =
 23 LIBTOOL_CLEAN   =
 24 LIBTOOL_LINK    = ${CC}
 25 LINK            = $(LIBTOOL_LINK)
 26 
 27 x               =
 28 o               = .o
 29 LOCAL_LIBDIR    = .
 30 
 31 CFLAGS          = -g -O2
 32 CPPFLAGS        = -DHAVE_CONFIG_H -I../include -I$(srcdir)/../include -I.  -D_GNU_SOURCE
 33 LDFLAGS         = -L.. -L/lib
 34 #
 35 #Agregar Nuevas piezas acá 
 36 #
 37 BINS    = \
 38         Tools$x\
 39         Inicio$x
 40 CKDKSRC = \
 41         Tools.c\
 42         Inicio.c
 43 
 44 LINKIT  = $(LINK) $(CFLAGS) $(CPPFLAGS) $? -o $@ $(LDFLAGS) $(LIBS)
 45 
 46 all : $(BINS)
 47 #
 48 #Agregar Nuevas piezas TAMBIEN acá 
 49 #
 50 
 51 Tools$x :               Tools.c         ; $(LINKIT)
 52 Inicio$x :              Inicio.c                ; $(LINKIT)
 53 #
 54 # Standard clean directives.
 55 #
 56 clean::
 57         -$(LIBTOOL_CLEAN) $(RM) *.o core $(BINS)
 58 
 59 distclean:: clean
 60         $(RM) Makefile
 61 
 62 #tags :
 63 #       $(CTAGS) *.[ch] */*.[ch]
 64 
 65 #TAGS :
 66 #       $(ETAGS) *.[ch] */*.[ch]
 67 
 68 lint: $(CDKSRC)
 69         $(LINT) $(LINT_OPTS) $(CPPFLAGS) $(CDKSRC)

```

and im getting this error when compiling 

```

kiltran@Olympus:~/MyDev/ncurses/cdk-5.0-20140118/DocTec$ make -f MakeDocTec 
gcc -g -O2  -DHAVE_CONFIG_H -I../include -I./../include -I.  -D_GNU_SOURCE Tools.c -o Tools -L.. -L/lib   -lcdk -lncurses 
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 0 tiene un índice de símbolo 11 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 1 tiene un índice de símbolo 12 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 2 tiene un índice de símbolo 2 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 3 tiene un índice de símbolo 2 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 4 tiene un índice de símbolo 11 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 5 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 6 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 7 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 8 tiene un índice de símbolo 12 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 9 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 10 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 11 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 12 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 13 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 14 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 15 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 16 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 17 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 18 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 19 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 20 tiene un índice de símbolo 13 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_info): la reubicación 21 tiene un índice de símbolo 22 inválido
/usr/bin/ld: /usr/lib/debug/usr/lib/i386-linux-gnu/crt1.o(.debug_line): la reubicación 0 tiene un índice de símbolo 2 inválido
/usr/lib/gcc/i686-linux-gnu/4.8/../../../i386-linux-gnu/crt1.o: En la función `_start':
(.text+0x18): referencia a `main' sin definir
collect2: error: ld returned 1 exit status
make: *** [Tools] Error 1



```

As you can see at the bottom, it sais main has no defined refferene .. but Tools.c has no main since is just a compilation of usefullo functions. 

Any ideas and tips would be much appreciated! 
Thanks in advace !
Regards. from Chile :D

Hi i've been developing a Qt app and i once forget write the main.cpp into .pro file and compiler send me that list of errors; then i write main.cpp into .pro and that fixed it. I hope that help you

Carlos from Mexico

---

