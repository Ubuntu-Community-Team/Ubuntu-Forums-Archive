---
title: "Python PIL 1.1.6 in Edgy"
date: 2007-01-03
forum: Programming Talk
---

### Post by irrelative on 2007-01-03
Hi everyone,

I'm trying to get the newest version of the python PIL (version 1.1.6), which fixes a bug with the width of a drawn line.  Edgy currently supports 1.1.5.

After getting all the dependencies (obscure dev libs -- jpeg, gzip, tkinter), I'm still getting the following problem when I try to install:

creating build/temp.linux-i686-2.4/Tk
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -IlibImaging -I/usr/include -I/usr/local/include -I/usr/include/python2.4 -c _imagingtk.c -o build/temp.linux-i686-2.4/_imagingtk.o
_imagingtk.c:20:16: error: tk.h: No such file or directory
_imagingtk.c:23: error: expected ‘)’ before ‘*’ token
_imagingtk.c:31: error: expected specifier-qualifier-list before ‘Tcl_Interp’
_imagingtk.c: In function ‘_tkinit’:
_imagingtk.c:37: error: ‘Tcl_Interp’ undeclared (first use in this function)
_imagingtk.c:37: error: (Each undeclared identifier is reported only once
_imagingtk.c:37: error: for each function it appears in.)
_imagingtk.c:37: error: ‘interp’ undeclared (first use in this function)
_imagingtk.c:45: error: expected expression before ‘)’ token
_imagingtk.c:51: error: ‘TkappObject’ has no member named ‘interp’
_imagingtk.c:55: warning: implicit declaration of function ‘TkImaging_Init’
error: command 'gcc' failed with exit status 1

I think I've installed everything, including Tkinter, but this isn't working.  Any thoughts are greatly appreciated.  Thanks!

Cheers,
Justin

---

