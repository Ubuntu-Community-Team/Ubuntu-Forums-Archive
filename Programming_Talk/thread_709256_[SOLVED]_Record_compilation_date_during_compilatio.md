---
title: "[SOLVED] Record compilation date during compilation"
date: 2008-02-27
forum: Programming Talk
---

### Post by Vadi on 2008-02-27
Hi,

I'd like my C program to be able to report the date it was compiled - like "This version was compiled on Feb 19th, 2008.". Is it possible to accomplish this somehow?

I'm using a Makefile for the compiling (and couldn't really find the needed info on the net).

---

### Post by WW on 2008-02-28
You can use the [predefined macros](http://gcc.gnu.org/onlinedocs/cpp/Standard-Predefined-Macros.html#Standard-Predefined-Macros) __TIME__ and __DATE__:


cdatetest.c:
```
#include <stdio.h>

int main(int argc, char *argv[])
{
printf("This program was compiled at %s on %s\n",__TIME__,__DATE__);
return 0;
}

```


Compile and run:
> 
$ gcc -Wall cdatetest.c -o cdatetest
$ ./cdatetest 
This program was compiled at 13:00:14 on Feb 28 2008
$ gcc -Wall cdatetest.c -o cdatetest
$ ./cdatetest 
This program was compiled at 13:01:51 on Feb 28 2008
$ 


---

### Post by Vadi on 2008-02-28
I didn't know about that. Thanks!

---

