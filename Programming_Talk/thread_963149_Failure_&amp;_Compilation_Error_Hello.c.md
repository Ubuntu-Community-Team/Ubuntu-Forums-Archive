---
title: "Failure &amp; Compilation Error Hello.c"
date: 2008-10-29
forum: Programming Talk
---

### Post by suredazzle on 2008-10-29
Hi,

Downloaded gcc-testsuite-4.3.2.

[http://gcc.releasenotes.org/releases/](http://gcc.releasenotes.org/releases/)

Try to run the file on Mac OS.

gcc -o hello.c
gcc -v hello.c

It returns command not found. Can you please tell me what's wrong?

#include <stdio.h>
main ()
{
printf("Hello World\n");
}

---

### Post by suredazzle on 2008-10-29
Any help is needed?

---

### Post by PandaGoat on 2008-10-30
You have to define main as a function.  It needs a return type and all that definition jazz.

#include <stdio.h>
int main()
{
printf("Hello World\n");
return 0;
}

---

### Post by WW on 2008-10-30
> **suredazzle said:**
> Hi,

Downloaded gcc-testsuite-4.3.2.

[http://gcc.releasenotes.org/releases/](http://gcc.releasenotes.org/releases/)

What do you mean?  Exactly what did you download, and what did you do with it?
> **suredazzle said:**
> 
Try to run the file on Mac OS.

gcc -o hello.c
gcc -v hello.c

It returns command not found. Can you please tell me what's wrong?

"command not found" means you don't have a **gcc** command.  So whatever you did, you have not successfully installed gcc.

---

