---
title: "strcmp doesn't exist?"
date: 2010-01-24
forum: Programming Talk
---

### Post by ownaginatious on 2010-01-24
Hello everyone.

I'm currently having a problem with the built in strcmp function and C. For some reason it's causing a segmentation fault in my program. I was able to track it as the source using gdb, and get the following:

```

Program received signal SIGSEGV, Segmentation fault.
strcmp () at ../sysdeps/x86_64/strcmp.S:30
30	../sysdeps/x86_64/strcmp.S: No such file or directory.
	in ../sysdeps/x86_64/strcmp.S


```

I'm confused as to what this means exactly. Is it trying to tell me that this function doesn't even exist? Sorry, I'm quite new to C.

Is there something I'm supposed to be doing besides #include <string.h> to get this to work?

Thanks.

---

### Post by cpplinux on 2010-01-24
It just means gdb cannot find the source code. Since strcmp is in the library, you didn't need its source code when you built your program. You didn't post your code so I can only guess that the segmentation fault is likely caused by over-boundary reading of the memory.

---

### Post by ibuclaw on 2010-01-24
If you are still not very aware of how C uses memory, it is usually a good idea to leave out optimisations. ;)
Chances am you are receiving that because you didn't initialise a variable properly, and compiled with -O2

Regards
Iain

---

### Post by ownaginatious on 2010-01-24
I figured out the error; it was elsewhere in the program (accidentally put the wrong index somewhere).

Thanks for the help; I would have wasted along time looking into this false missing strcmp thing gdb reported otherwise.

---

