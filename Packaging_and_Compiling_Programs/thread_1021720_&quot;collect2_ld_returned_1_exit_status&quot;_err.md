---
title: "&quot;collect2: ld returned 1 exit status&quot; error when compiling C with GCC"
date: 2008-12-25
forum: Packaging and Compiling Programs
---

### Post by justrasputin on 2008-12-25
For some reason, I see the following when I try to compile any C code involving the math.h header file, e.g.

```
rasputin@rasputin-laptop:~/Documents/euler/c$ gcc p012.c
/tmp/ccaN3FGJ.o: In function `main':
p012.c:(.text+0xa7): undefined reference to `sqrt'
collect2: ld returned 1 exit status
```

This happens with any function in math.h, and yes, I have written

```
#include <math.h>
```

math.h exists in /usr/share, and the other header files I've used (stdlib, stdio, string) are in there as well.

I can compile it by adding the -lm argument to link the math library, but I dislike having to do that.

I tried removing and reinstalling build-essentials, didn't help.

I've googled this for a while, all the solutions I found were simply adding the -lm tag, or using g++ (which, by the way, does not need the -lm argument).

If anyone could point me in the right direction, I'd appreciate it.

---

### Post by coleslow on 2009-05-14
i thought it was #include <cmath> in c++

---

### Post by lisati on 2009-05-14
> **coleslow said:**
> i thought it was #include <cmath> in c++
I gather from the OP's query that it's a C program, otherwise it would probably be a .cpp file and the g++ compiler.....

---

