---
title: "Compiling Tcl/Tk from source"
date: 2009-01-30
forum: Packaging and Compiling Programs
---

### Post by yanom on 2009-01-30
I built Tcl to the directory /home/yanom/tcl-tk/ , then run this command to try to build tk into that directory:

```

$   ./configure --prefix=/home/yanom/tcl-tk/ --with-tcl=/home/yanom/tcl-tk/lib/ && make && make install

```

it gives a LOOOOOOOOOOOOOOOOOOOOOOOOOONNNNNNNNNNNNGGGG output but here is the last bit:

```
/home/yanom/tk8.5.6/unix/../generic/tkDecls.h:1983: error: declaration for parameter ‘TkStubs’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tkDecls.h:1703: error: declaration for parameter ‘TkStubHooks’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk.h:1431: error: declaration for parameter ‘Tk_ElementSpec’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk.h:1411: error: declaration for parameter ‘Tk_ElementOptionSpec’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk.h:1298: error: declaration for parameter ‘Tk_PhotoImageFormat’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk.h:1283: error: declaration for parameter ‘Tk_PhotoImageBlock’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk.h:1266: error: declaration for parameter ‘Tk_PhotoHandle’ but no such parameter
/home/yanom/tk8.5.6/unix/../generic/tk3d.c:1387: error: expected ‘{’ at end of input
make: *** [tk3d.o] Error 1

```

why can't I build the library?

---

