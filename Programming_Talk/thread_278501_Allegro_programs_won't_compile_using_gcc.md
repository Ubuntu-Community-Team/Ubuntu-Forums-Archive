---
title: "Allegro programs won't compile using gcc"
date: 2006-10-16
forum: Programming Talk
---

### Post by nissem on 2006-10-16
I have installed Allegro and started playing around with it. The problem is that I can't compile even the Vivace examples. It works using the makefile that came with the examples so there shouldn't really be a problem.
For example: The first example in chapter 5 which draws a circle that moves across the screen. There are four files: 051s.c, 051sc.c and their .h files. Trying ```
gcc 051sc.c `allegro-config --cflags` `allegro-config --libs`
```
Gives the error:
```
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

```
And compiling the 051s.c files gives the follwing:
```
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
martin@ubuntubox:~/dokument/programmering/c/moveFigProg$ gcc 051s.c `allegro-config --cflags` `allegro-config --libs`
/tmp/ccQ0pS1U.o: In function `init':051s.c:(.text+0x1ca): undefined reference to `circle_init'
:051s.c:(.text+0x20c): undefined reference to `circle_draw'
/tmp/ccQ0pS1U.o: In function `process':051s.c:(.text+0x257): undefined reference to `circle_update'
/tmp/ccQ0pS1U.o: In function `output':051s.c:(.text+0x276): undefined reference to `circle_erase'
:051s.c:(.text+0x28d): undefined reference to `circle_draw'
/tmp/ccQ0pS1U.o: In function `shutdown':051s.c:(.text+0x2a7): undefined reference to `circle_destroy'
collect2: ld returned 1 exit status

```

The gcc command that I used was found here in the forums. Using a simple ```
gcc -o -lalleg 051s.c 
``` Gives a hughe number of undefines references:
```
....
:051s.c:(.text+0xb0): undefined reference to `allegro_error'
:051s.c:(.text+0xbc): undefined reference to `allegro_message'
:051s.c:(.text+0xcd): undefined reference to `gfx_driver
... 
``` etc.

What am I doing wrong??

Thankfull for help!

---

### Post by duff on 2006-10-16
> **nissem said:**
> 
Gives the error:
```
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

```

That looks like you're trying to create an executable program without a **main** function.  Is this a program or a library?

> The gcc command that I used was found here in the forums. Using a simple ```
gcc -o -lalleg 051s.c 
``` 

Either loose the '-o' parameter or supply a destination file. eg,```
gcc -o 051s -lalleg 051s.c
```

---

### Post by nissem on 2006-10-16
Thanks a lot for the quick answer, I appreciate it! But it did not help me. Using gcc your way only gave me the same massive "undefined reference":es. 
051s.c is a simple executable that shows a circle moving across the screen and the functions for the cirlce are located in 051sc.c. This means ofcourse that 051sc.c doesn't have a main and can't be compiled thefore but the problem still remains for the 051s.c :(

---

