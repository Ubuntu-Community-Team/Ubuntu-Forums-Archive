---
title: "What is wrong with my static library?"
date: 2010-04-15
forum: Programming Talk
---

### Post by PanP5 on 2010-04-15
I have 5 files, 3 are .cpp, 2 are corresponding .h

```
a.cpp

b.cpp
b.h

c.cpp
c.h
```

b depends on c. a depends on b and c.

When I use the following g++ command, it compiles without a hitch, and the executable runs perfectly:

```
g++ -o output c.cpp b.cpp a.cpp -lpthread
```

Now I want to throw c and b into a static library. So I do the following. First I generate c.o and b.o:

```
g++ -c c.cpp
g++ -c b.cpp
```

Then I use ar to throw them into the static library:

```
ar rcs lib_e.a b.o c.o
```

Then I move lib_e.a and a.cpp into a separate folder.

I cd into that folder, and attempt to create an executable:

```
g++ -static -l lib_e.a -o output a.cpp -lpthread
```

The compiler issues all sorts of errors. It can't see b.h or c.h. What did I do wrong?

---

### Post by MadCow108 on 2010-04-15
if you move the files to a different folder you have to adapt the include directory

-Idir

As you have compiled a static library you don't necessarily need the -static flag.
-static prevents linking with otherwise shared libraries (which yours is not according to your post).
So only use it if you really want a non dynamic executable (=static libc etc which really bloats the executable)

and the -l flag needs the name without space, lib and extension:
-l_e links lib_e.a
(you see the underscore does probably not conform to unix library naming)

the flag for pthread is -pthread not -lpthread

---

### Post by PanP5 on 2010-04-15
> **MadCow108 said:**
> if you move the files to a different folder you have to adapt the include directory

-Idir

As you have compiled a static library you don't necessarily need the -static flag.
-static prevents linking with otherwise shared libraries (which yours is not according to your post).
So only use it if you really want a non dynamic executable (=static libc etc which really bloats the executable)

and the -l flag needs the name without space, lib and extension:
-l_e links lib_e.a
(you see the underscore does probably not conform to unix library naming)

the flag for pthread is -pthread not -lpthread

This seems to have helped a bit.

I remade the library, naming it libenum.a. Then I moved it into the separate folder with a.cpp, b.h, and c.h. I tried to compile, but it complained that it couldn't find -lenum in /usr/bin/ld.

So I added -L. to the command, making it:

```
g++ -L. -lenum -o output a.cpp -pthread
```

It still is having trouble finding information in b and c, but it's different this time. Where as before the compiler was giving line numbers pointing to where the error was, now it gives

```
a.cpp:(.text+0xa0): undefined reference to `myFunction(void *)'
```

in the code, myFunction is the function I pass as the third argument of pthread_create. It is declared and defined in b.h and b.cpp

Any ideas?

---

### Post by MadCow108 on 2010-04-15
when doing static linking the order on the command line is important
if A depends on B, A must be before B so the needed symbols are known before it parses the file containing the definitions
try placing -lenum behind a.cpp
if you have cyclic dependencies you may even have to add a library twice on the command line

an alternative is the linker flag -Wl,--start-group files -Wl,--end-group
but it is very slow for big numbers of libraries

---

### Post by PanP5 on 2010-04-15
> **MadCow108 said:**
> when doing static linking the order on the command line is important
if A depends on B, A must be before B so the needed symbols are known before it parses the file containing the definitions
try placing -lenum behind a.cpp

```
g++ a.cpp -L. -lenum -o output -pthread
```

IT WORKED!

Thank you!

---

