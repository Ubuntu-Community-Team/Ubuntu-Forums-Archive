---
title: "C: undefined reference to `poptGetContext', library file in place, still not working"
date: 2013-01-09
forum: Programming Talk
---

### Post by vincent_kelly on 2013-01-09
Hi all, 

I'm trying to install a program in ubuntu 12.04 LTS. 
The files are attached. The main program calls the popt library. I did install the library. The library was originally in /usr/lib/i386-linux-gnu/. It didn't work. I wasn't sure if this was the folder where gcc would look for the libraries. So I made a sym link at /usr/lib/libpopt.so, which points to the original library file. 

But it still gives me these errors. 

```
acm@acm-desktop:~/Downloads/dat2dxf-0.8.3a$ make
gcc -o dat2dxf -Wall -O2 -DDEBUG -lpopt main.o point.o
main.o: In function `main':
main.c:(.text.startup+0x1fc): undefined reference to `poptGetContext'
main.c:(.text.startup+0x206): undefined reference to `poptGetNextOpt'
main.c:(.text.startup+0x293): undefined reference to `poptFreeContext'
main.c:(.text.startup+0x539): undefined reference to `poptPeekArg'
main.c:(.text.startup+0x54f): undefined reference to `poptGetArg'
main.c:(.text.startup+0x630): undefined reference to `poptStrerror'
main.c:(.text.startup+0x642): undefined reference to `poptBadOption'
collect2: ld returned 1 exit status
make: *** [dat2dxf] Error 1
```


Does anyone have idea what went wrong?

Thanks.

Vincent

---

### Post by steeldriver on 2013-01-09
try changing the link order

```
gcc -o dat2dxf -Wall -O2 -DDEBUG main.o point.o [COLOR=Red]-lpopt[/COLOR]
```

---

### Post by vincent_kelly on 2013-01-09
> **steeldriver said:**
> try changing the link order

```
gcc -o dat2dxf -Wall -O2 -DDEBUG main.o point.o [COLOR=Red]-lpopt[/COLOR]
```
Wow that's a quick reply, 
Too bad I just left my lab , have to wait until I wake up tomorrow morning to try it,

Thanks 
Vincent

---

### Post by dwhitney67 on 2013-01-10
> **steeldriver said:**
> try changing the link order

```
gcc -o dat2dxf -Wall -O2 -DDEBUG main.o point.o [COLOR=Red]-lpopt[/COLOR]
```

That's correct; libraries should be specified at the end of the statement when linking.

However, the compiler flags -Wall and -DDEBUG are unnecessary when performing this step.  They are only used when compiling the source code.  Once the object files have already been created, they are no longer necessary.

---

### Post by vincent_kelly on 2013-01-10
> **dwhitney67 said:**
> That's correct; libraries should be specified at the end of the statement when linking.

However, the compiler flags -Wall and -DDEBUG are unnecessary when performing this step.  They are only used when compiling the source code.  Once the object files have already been created, they are no longer necessary.
Thanks guys! It works! 

Sounds like a common rule to put the library at the end. I'll keep that in mind. 

And about the compiler flags, is -O2 necessary in this step?

---

### Post by steeldriver on 2013-01-10
The rule is a bit more complicated than that

If module 'A' (which can be either an object file or another library) uses symbols from module 'B', then the order on the link line needs to be A B (i.e. kind of 'from most to least')

There are special options for resolving circular references - but if you're lucky you will never need to use them

I *think* that the '-Ox' optimization flags only apply to the compile phase - but there may be some link time optimization (LTO) subtleties that I'm unaware of - gcc is a huge complicated beast

Hope that helps

---

### Post by vincent_kelly on 2013-01-10
> **steeldriver said:**
> The rule is a bit more complicated than that

If module 'A' (which can be either an object file or another library) uses symbols from module 'B', then the order on the link line needs to be A B (i.e. kind of 'from most to least')

There are special options for resolving circular references - but if you're lucky you will never need to use them

I *think* that the '-Ox' optimization flags only apply to the compile phase - but there may be some link time optimization (LTO) subtleties that I'm unaware of - gcc is a huge complicated beast

Hope that helps
Thanks for the explanation.

---

