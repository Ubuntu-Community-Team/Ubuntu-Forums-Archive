---
title: "Compiling C Code in Ubuntu GNOME Terminal"
date: 2009-01-05
forum: Programming Talk
---

### Post by throlkena on 2009-01-05
Hi, I am new to using the C Compiler in linux.

Now, this is my problem really:

//i am trying to compile this: a.c

#include <stdio.h>
#include <sys/types.h>

int main()
{
fork();
print("Hello Fork!\n");
}



//then i compile and link using : gcc -o proc1 a.c
//then run as ./proc1


//the errors:

/*
a.c:1:20: error: stdio.h: No such file or directory
a.c:2:22: error: sys/types.h: No such file or directory
a.c: In function ‘main’:
a.c:7: warning: incompatible implicit declaration of built-in function ‘printf’
*/


If anyone knows how to workaround this, or if there's anyother way to do this, please do let me know,

This worked in a terminal i used at university, but it doesn't work in the emulator on my laptop.

---

### Post by Zugzwang on 2009-01-05
Please read the stickies. There's a link somewhere on "how to compile your first C program".

---

### Post by mali2297 on 2009-01-05
Have you installed the package **build-essential**?

---

