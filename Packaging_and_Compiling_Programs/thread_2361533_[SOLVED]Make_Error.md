---
title: "[SOLVED]Make Error"
date: 2017-05-17
forum: Packaging and Compiling Programs
---

### Post by Floppyjoe on 2017-05-17
I get this error when issuing the make command while compiling a program:
```
/usr/bin/ld: eggtrayicon.o: undefined reference to symbol 'XFlush'
//usr/lib/x86_64-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line
```

Does anyone know what to change in the makefile to get it to compile?

---

### Post by steeldriver on 2017-05-17
Add

```

-lX11

```

to the link command maybe? It's hard to be more specific without seeing the Makefile - look for a LIBS or LDFLAGS variable

---

### Post by Floppyjoe on 2017-05-17
> **steeldriver said:**
> Add

```

-lX11

```

to the link command maybe? It's hard to be more specific without seeing the Makefile - look for a LIBS or LDFLAGS variable

Do you need to change all the Makefiles in every directory because this does not work doing it just in the main directory.

---

### Post by steeldriver on 2017-05-17
It's hard to say without knowing the Makefile structure - you could try passing

```

make "LDFLAGS=-lX11"

```

on the command line - but there's no guarantee it will be used everywhere. Is the software you are trying to build publicly available? if so, please post a link so we can take a look at it.

---

### Post by Floppyjoe on 2017-05-17
> **steeldriver said:**
> It's hard to say without knowing the Makefile structure - you could try passing

```

make "LDFLAGS=-lX11"

```

on the command line - but there's no guarantee it will be used everywhere. Is the software you are trying to build publicly available? if so, please post a link so we can take a look at it.

Thank you that worked!

---

