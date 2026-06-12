---
title: "Segmentation Fault on Ubuntu 9.10, x64"
date: 2010-08-17
forum: Programming Talk
---

### Post by tyliew333 on 2010-08-17
Hey guys,

I have been facing a problem for a week and yet I still could not get  any solutions. I have a piece of C code which containing malloc(). I  compile the same C code and run on 2 different machines, one is Ubuntu  10.04 (32 bit) while another machine is Ubuntu 9.10 (64 bit). When I  compile and run on Ubuntu 10.04 (32 bit). It worked fine.  But when I  compile and run on Ubuntu 9.10 (64 bit), it gave me Segmentation fault  whenever it reaches malloc () in my C code. 

I'm new to ubuntu, anyone can tell me where lies the problems and solutions?

Thank in advance.

regards, tyliew

---

### Post by MadCow108 on 2010-08-17
no one can really help not without sample code.

You can use tools gdb and/or valgrind to debug the problem yourself if you are unwilling to share.

---

### Post by tyliew333 on 2010-08-17
Enclosed is the sample code.

---

### Post by Lootbox on 2010-08-17
I think you want to change:
```
arrayOriPad= (unsigned int **) malloc ( (5)*sizeof(unsigned int));
```
to:
```
arrayOriPad= (unsigned int **) malloc ( (5)*sizeof(unsigned int*));
```

i.e. since arrayOriPad is a pointer to an unsigned int pointer.

[edit] I forgot to mention: I ran it, it seg-faulted. After I made that change, there were no issues.

---

### Post by dwhitney67 on 2010-08-17
Here's the problem in your code:
```

arrayOriPad= (unsigned int **) malloc ( (5)*sizeof(unsigned int) );

```
Should be:
```

arrayOriPad= (unsigned int **) malloc ( (5)*sizeof(**unsigned int***) );

```
Note that you need to allocate an array of pointers; not just ints.  An int on a 32-bit system occupies 4-bytes, and by coincidence so does a pointer.  However, on a 64-bit system, a pointer occupies 8-bytes.

---

### Post by tyliew333 on 2010-08-17
Yes, it works after changing the code. There is a bug in my code. I didn't realize in 64 bit system, pointer takes 8 bytes. Thanks you very much.

---

### Post by trent.josephsen on 2010-08-17
Prefer the form

```
arrayOriPad= malloc( 5*sizeof *arrayOriPad );
```

Using the thing you want to allocate in the argument to sizeof makes it less error prone when you later change arrayOriPad to struct some_complex_structure *.

Don't cast the return from malloc(); it can hide helpful warnings if you ever forget to #include <stdlib.h>, and it doesn't buy you anything (malloc() is guaranteed to return a pointer of proper alignment for any type, and the conversion is performed automatically per regular assignment rules).

---

