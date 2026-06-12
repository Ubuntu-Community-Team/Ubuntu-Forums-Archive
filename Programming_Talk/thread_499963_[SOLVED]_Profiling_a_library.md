---
title: "[SOLVED] Profiling a library"
date: 2007-07-13
forum: Programming Talk
---

### Post by WebDrake on 2007-07-13
Hello all,

I've been working on a small library that is built using the GNU autotools.  I would like to profile its performance to check where are the slow points in the code but can't work out how.  When building the library I use,

```
./configure CFLAGS="-O2 -pg"
```

... but I am unable to get meaningful input out of gprof after running simulations with the library.  If I run gprof on an object file, I get no data on used functions while if I run it on the library (libminga.la) or the executable created and run, I get a message: "not in executable format".

Clearly I'm doing something very wrong so I wonder if someone can explain how I can effectively profile my library using gprof (or something else).

---

### Post by hod139 on 2007-07-13
I would suggest using callgrind to to profile your code.  The commands differ between dapper and feisty however.  On dapper, callgrind is a separate tool, whereas on feisty it is integrated within valgrind.  I am running dapper, so I would do 
```

callgrind ./a.out

```
which will produce a file call callgrind.out.#####

This file is not very readable by a human, but the program kcachegrind (also install graphviz to get some fancy looking callgraphs) is excellent for reading it.
```

kcachegrind callgrind.out.#####

```

---

### Post by WebDrake on 2007-07-13
> **hod139 said:**
> I would suggest using callgrind to to profile your code.  The commands differ between dapper and feisty however.  On dapper, callgrind is a separate tool, whereas on feisty it is integrated within valgrind.  I am running dapper, so I would do 
```

callgrind ./a.out

```
which will produce a file call callgrind.out.#####

This file is not very readable by a human, but the program kcachegrind (also install graphviz to get some fancy looking callgraphs) is excellent for reading it.
```

kcachegrind callgrind.out.#####

```

Thanks for the heads-up on the program. :)

It wasn't an issue of the profiler, it turned out to be the configuration of GNU autotools when building it: I had to ensure the library was built as static.  So,

```
./configure --disable-shared
```

```
make clean all CFLAGS="-pg"
```

and then after running foo, call gprof via libtool:

```
./libtool --mode=execute gprof ./foo
```

Thanks to the libtool mailing list for providing the solution. :)

---

### Post by hod139 on 2007-07-13
Callgrind will profile dynamic libraries, as you found out gprof does not.  This is one reason I prefer callgrind.

---

### Post by WebDrake on 2007-07-13
> **hod139 said:**
> Callgrind will profile dynamic libraries, as you found out gprof does not.  This is one reason I prefer callgrind.

Ah!  That's a bonus.  Thanks again. :)

*EDIT:* I've been playing around with valgrind and kcachegrind a bit---what a fun piece of kit!  It already alerted me to some memory leaks I had been unaware of and provided a lot of useful profiling information.  The thanks just keep coming.

---

### Post by hod139 on 2007-07-13
No problem, I'm glad it has helped.  I don't know how I survived all those years before discovering valgrind and callgrind.

---

