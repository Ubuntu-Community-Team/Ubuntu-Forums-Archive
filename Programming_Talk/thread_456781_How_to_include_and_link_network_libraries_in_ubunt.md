---
title: "How to include and link network libraries in ubuntu?"
date: 2007-05-28
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-28
Hi,

I need to include the following .h in my code:

#include <netdb.h>
#include <netinet/in.h>
#include <unistd.h>

What do I need to do in my makefile to include and link network libraries in ubuntu?

---

### Post by neskie on 2007-05-28
If I knew the answer I'd tell you right here and now, but I have an even better solution.  You can download the Advanced Linux Programiing which is at

[http://www.advancedlinuxprogramming.com/](http://www.advancedlinuxprogramming.com/)

It's released under the Open Publication License and brings you through the whole process of building command line tools for GNU/Linux.  The final project is desiging a simple HTTP server.

---

### Post by ruy_lopez on 2007-05-28
You shouldn't have to do anything. Just  #include "your.h" in your main.c, where your.h is the header where the network headers are included. You shouldn't need any compiler flags for these.

the makefile would look something like this:

```
PROGS = yourprogram

yourprogram : 
                 gcc -Wall -o $@ main.c

clean:
                 rm -rf ${PROGS} *.o

```
If there are other object files, just add them after yourprogram:, and after the main.c, the compiler should take care of them.

---

### Post by christhemonkey on 2007-05-28
Also if you want it to succesfully compile,
Once you have set up your makeful,
Make sure you have libc6-dev installed as this library actually contains those header files you are trying to link to.

---

