---
title: "how to use levmar-2.4"
date: 2009-06-14
forum: Programming Talk
---

### Post by santhust on 2009-06-14
Hi. 
I am trying to use levmar2.4 in ubuntu. i have looked into the synaptic pacakage manager and has installed lblas, llapack, libf2c2-dev. I have also downloaded levmar-2.4. Now I am trying to compile Makefile in this levmar2.4 folder. However it is returning some error message, which is shown below:


make -k 
gcc -L/usr/local/lib  -L. lmdemo.o -o lmdemo -llevmar -llapack -lblas -lf2c  -lm
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/libf2c.so: undefined reference to `MAIN__'
collect2: ld returned 1 exit status
make: *** [lmdemo] Error 1
make: Target `all' not remade because of errors.

Compilation exited abnormally with code 2 at Sun Jun 14 14:19:45


Can someone help me please. Alternatively can someone help me how to use levmar.
Any help will be greatly appreciated.

---

### Post by Burmuda on 2009-07-07
Had the same problem. Further searching the internets revealed:

pass the option -u MAIN__ to the linker

So this worked for me:

gcc -L/usr/local/lib  -L. lmdemo.o -o lmdemo -llevmar -llapack -lblas -lf2c  -lm -u MAIN__

---

