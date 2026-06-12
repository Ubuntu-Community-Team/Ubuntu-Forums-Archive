---
title: "Help manually linking object files using  &quot; ld &quot; or &quot;gold&quot;"
date: 2012-07-24
forum: Programming Talk
---

### Post by vikkyhacks on 2012-07-24
[CENTER]<< I am using linux gcc compiler >>[/CENTER]

#include<stdio.h>
void main()
{
printf("Hello !!!");
}

I get the object file of this source code using the command **cc -c hello.c**. I compile it using the the command cc *hello.c* and get* hello.out,* i find that it needs */lib/i386-linux-gnu/libc.so.6* and */lib/ld-linux.so.2 library* (using command ldd hello.out) and therefore  i try to LINK using the command **ld  /lib/i386-linux-gnu/libc.so.6 /lib/ld-linux.so.2 hello.o** but i get an error
** ld: warning: cannot find entry symbol _start; defaulting to 00000000080481b4**
HELP ME !!! How do i link my program ... ??? :confused:
( I know that just typing cc a.c will automatically link compile and do everything in a simple way ... I have to do symbol table manipulation and some other stuffs !!! .... Therefore I need to learn how to link object files to libraries MANUALLY )

---

### Post by Bachstelze on 2012-07-24
> **vikkyhacks said:**
> I have to do symbol table manipulation and some other stuffs !!!

Why? If you have to ask this question, you do not possess the knowledge to do that kind of thing. I (or Google) could give you a command to copy-and-paste, but it wouldn't really help you.

---

