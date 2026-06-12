---
title: "Running compiled *.C files"
date: 2013-02-24
forum: Programming Talk
---

### Post by TheBigBadWolf on 2013-02-24
Hey! So, after finishing my first test *.c (hello world) in Gedit, I made it an executable with the terminal via 
make ex1

and it created the executable ex1. But if I execute it, it does nothing.
Is that normal? did I not understand something essential?
Just to mention it again.. this is my first day on Linux!

---

### Post by QIII on 2013-02-24
*Moved to** Programming Talk***

---

### Post by matt_symes on 2013-02-24
Hi

Did you compile it using gcc ?

Kind regards

---

### Post by Gyokuro on 2013-02-24
Mabe you can post your file(s) as I assume you have a helloworld.c and a Makefile. Otherwise compile it via:

gcc -o helloworld yourcfile.c  (yourcfile.c is a placeholder for your C file) 

Happy coding!

---

### Post by r-senior on 2013-02-24
If you ran make on your program, you probably compiled it with gcc, which is the default C compiler for GNU/Linux.

Here's a transcript of compiling a little hello world program. See if you can spot any differences from what you did:

```

$ cat hello.c
#include <stdio.h>

int main()
{
    puts("Hello World");
}
$ make hello
cc     hello.c   -o hello
$ ./hello
Hello World
$
```

The "$" sign is not for you to type -- it represents the prompt in a terminal. The other stuff is the output I got from the commands I typed.

---

### Post by trent.josephsen on 2013-02-24
If TheBigBadWolf used `make' and didn't get an error message, I think we can assume it was successfully compiled... And you don't need a Makefile to build an executable with make.

---

### Post by TheBigBadWolf on 2013-02-24
Thanks, yes I used gcc and I rewrote it and a few other scripts, and tried some other approaches to compiling, just to test the compiler, and now, miraculously, it works.

Thanks, and sorry for prematurely asking for help.. But you helped!

---

