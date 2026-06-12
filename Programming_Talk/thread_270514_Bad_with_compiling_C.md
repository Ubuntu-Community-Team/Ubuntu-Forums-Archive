---
title: "Bad with compiling C"
date: 2006-10-03
forum: Programming Talk
---

### Post by namai on 2006-10-03
Hi, i have a problem with compiling c program.
There is a simple program code:
----------------------------------------------------------------
#include <math.h>

	main()

	{ int i;

	   printf("\t Number \t\t Square Root of Number\n\n");

	   for (i=0; i<=360; ++i)
            printf("\t %d \t\t\t %d \n",i, sqrt((double) i));

	}
----------------------------------------------------------------

..and here is a problem of compiling:
----------------------------------------------------------------
namai@namai-desktop:~/c$ cc prog.c
prog.c:1:18: error: math.h: No such file or directory
prog.c: In function ‘main’:
prog.c:7: warning: incompatible implicit declaration of built-in function ‘printf’
prog.c:10: warning: incompatible implicit declaration of built-in function ‘sqrt’
namai@namai-desktop:~/c$
---------------------------------------------------------------
I use daper 64. :-k

---

### Post by pufuwozu on 2006-10-03
You have to include stdio.h to get printf to work. To get sqrt to work you have to link the program against the math library, to do this you need to add the lm flag to the compiling options.

Add this to the top of prog.c:
#include <stdio.h>

Change this to your compile command:
cc prog.c -lm

Then run it with:
./a.out

---

### Post by namai on 2006-10-03
ok, i tried, but there is a other problem:
--------------------------------------------------------
namai@namai-desktop:~/c$ cc -lm prog.c
prog.c:1:19: error: stdio.h: No such file or directory
prog.c:2:18: error: math.h: No such file or directory
prog.c: In function ‘main’:
prog.c:8: warning: incompatible implicit declaration of built-in function ‘printf’
prog.c:11: warning: incompatible implicit declaration of built-in function ‘sqrt’
namai@namai-desktop:~/c$
---------------------------------------------------------
I think there is a problem with gcc or libs..:-k

---

### Post by Roptaty on 2006-10-03
It looks to me that you havent installed libc6-dev package. Please install the build-essential metapackage by synaptic or sudo apt-get install build-essential.

---

### Post by namai on 2006-10-04
Its work. Thank you:-D

---

### Post by fyz on 2006-10-04
> **Roptaty said:**
> It looks to me that you havent installed libc6-dev package. Please install the build-essential metapackage by synaptic or sudo apt-get install build-essential.

Hi there,
I am new to linux. I am trying to programming c++ under ubuntu linux. (I have some experiences of programming under MS Windows.)

What is "build-essential"?
How to set up the Environment in order to compile, debug the source code?

Thanks!

---

### Post by Ayman on 2006-10-04
> What is "build-essential"?

It is a meta package that installs compilers and build tools, to install it, open a terminal and run:
```
$ sudo apt-get install build-essential
```

After that, you will be able to compile C++ progams with the following command:
```
$ g++ main.cpp -o main
```

If you want a development environmant, check out Anjuta:
[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

You can install it by running:
```
$ sudo apt-get install anjuta
```

---

### Post by fyz on 2006-10-04
Thanks a lot!

> **Ayman said:**
> ```
What is "build-essential"?
```

It is a meta package that installs compilers and build tools, to install it, open a terminal and run:
```
$ sudo apt-get install build-essential
```

---

