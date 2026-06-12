---
title: "Compiling Problems"
date: 2007-07-12
forum: Programming Talk
---

### Post by qcfpunch on 2007-07-12
Hey guys, I'm a linux newbie having only successfully installed kubuntu 2 days ago and a total programming newbie, having only picked up my first C book today. I'm having a problem compiling a simple piece of code, the standard "Hello, this is my first C program", basically copied out of the textbook. Whenever I try to compile, it displays: 

02l01.c:1:19: error: stdio.h: No such file or directory
02l01.c: In function &#8216;main&#8217;:
02l01.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

Can anyone explain what's wrong?

My code looks like this:

#include <stdio.h>

main ()
{
        printf ("Howdy, neighbour! This is my first C program.\n");
        return 0;
}

Any help would be greatly appreciated.

Regards,

qcfpunch

---

### Post by fishpie on 2007-07-12
Hi,

My C programming is very rusty, but I think the problem is that you need to install the package containing the stdio.h header file. Try using ```
apt-get install libc6-dev
``` and then try compiling again.

---

### Post by qcfpunch on 2007-07-12
It compiles now, thanks fishpie!

---

### Post by Rui Pais on 2007-07-12
Installing the compiler or parts of it  manually may lead to later problems (more headers not find, or "compiler cannot create executable" errors).

You must install it with:
```
sudo apt-get install build-essential
```
that would install all needed (libc, gcc...)

---

### Post by LaRoza on 2007-07-12
build-essential also has g++, so you can compile C++ programs.

Also when posting code on the forum, if you put it between the [ code ] [ /code ] tags, it is easier to read, and you formatting is preserved.

---

