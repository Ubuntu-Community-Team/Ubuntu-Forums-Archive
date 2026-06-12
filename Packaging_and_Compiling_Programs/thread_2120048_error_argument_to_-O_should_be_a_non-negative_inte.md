---
title: "error: argument to -O should be a non-negative integer"
date: 2013-02-25
forum: Packaging and Compiling Programs
---

### Post by tomzie on 2013-02-25
I wanted to try the same program that I am running in the SCO 5.05 environment into the Ubuntu server 12.04. However, in order to me to run it, I have to recompile the libraries. Here is the error I am getting when I try to recompile the libraries with *.a
 
$ make -f mlib.rmk
cc -c -Oactl -DPERFORMANCE string.c
cc1: error: argument to '-O' should be a non-negative integer
make: *** [string.o] Error 1
 
Inside mlib.rmk, I have this:
 
libdb5.a:    string.o entry.o allget.o
     ar -ruv libdb5.a *.o
 
.c.o:
         cc -c -Oactl -DPERFORMANCE $*.c
 
io.o:             io.c my.h dbc.h myfprot.h
 
I have only typed the first few objects *.o above, but I have more. Please help. Thanks.
 
Regards,
Sam

---

### Post by oldos2er on 2013-02-25
Moved to Packaging and Compiling Programs.

---

### Post by schragge on 2013-02-25
Well, the error message says it all. -O option in GCC takes numeric values. You can try
```

cc -c -O2 -DPERFORMANCE $*.c

```
But the best course would be to check what -Oactl does in SCO compiler, and then enable similar optimizations for GCC.

---

### Post by schragge on 2013-02-25
So, if the optimization flags for SCO UNIX 5.05 are still the same as for XENIX 286, then their meaning is

d - Default. Disables optimization
a - Relaxes alias checking
s - Optimizes code for space
t - Default. Optimizes code for speed
x - Performs maximum optimization. Equivalent to -Oactl
c - Eliminates common expressions
l - Performs various loop optimizations

I guess, in order to emulate -Oactl on GCC you can try something like
```
gcc -c -O2 -fpredictive-commoning -funswitch-loops -DPERFORMANCE $*.c
```

---

