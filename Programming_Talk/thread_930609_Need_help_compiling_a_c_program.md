---
title: "Need help compiling a c program"
date: 2008-09-26
forum: Programming Talk
---

### Post by Despot Despondency on 2008-09-26
Hey. My supervisor has given me a c program to run but I'm having difficulty compiling it. The source code is in a file called PopDynamics.c. The begining of the file is as follows

```

// gcc -O4 -o PopDynamics PopDynamics.c /home/tj/Documents/Programming/nrutil.c /home/tj/Documents/Programming/mt19937.c /home/tj/Documents/Programming/gauher.c   -lm

#include <stdio.h>

#include <math.h>

#include "/home/tj/Documents/Programming/nrutil.h"

```

All the files are in the given directory and when I run 

```

cc -c PopDynamics.c

```

Everything seems to go OK. I then run 

```

cc -o PopDynamics PopDynamics.c  -lm

```

but I get the following errors

```

/tmp/ccuElUBR.o: In function `init':
PopDynamics.c:(.text+0xddc): undefined reference to `genrand'
PopDynamics.c:(.text+0xe0a): undefined reference to `genrand'
/tmp/ccuElUBR.o: In function `PopDyn':
PopDynamics.c:(.text+0xe59): undefined reference to `genrand'
PopDynamics.c:(.text+0xe94): undefined reference to `genrand'
PopDynamics.c:(.text+0xebb): undefined reference to `genrand'
/tmp/ccuElUBR.o:PopDynamics.c:(.text+0x1100): more undefined references to `genrand' follow
collect2: ld returned 1 exit status


```

I don't understand why. The functions 'genrand' is defined in the file /home/tj/Documents/Programming/mt19937.c, so why doesn't it recognise it? Please help :(

---

### Post by issih on 2008-09-26
See that line commented out at the top of the text you pasted...I suspect that is the command it is suggesting you run to compile the program:

i.e. run:
```

gcc -O4 -o PopDynamics PopDynamics.c /home/tj/Documents/Programming/nrutil.c /home/tj/Documents/Programming/mt19937.c /home/tj/Documents/Programming/gauher.c   -lm
```

This way you will note that the file specifying the missing function is in the list of files to be compiled and linked...so things are likely to work

Hope that helps

P.S. The program will go a lot quicker using that line too, as its using the optimisations the compiler offers in the O4 option.

---

### Post by Despot Despondency on 2008-09-26
That seems to have done it. Cheers. Afraid I only know java at the moment and I don't have time to learn c at the moment as my project is due in on Wednesday. Cheers again

---

### Post by DrMega on 2008-09-26
If you put that long command into a make file, then next time you compile it you just need to run make:)

---

