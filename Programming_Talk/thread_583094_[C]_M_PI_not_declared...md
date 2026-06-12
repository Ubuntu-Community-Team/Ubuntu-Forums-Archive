---
title: "[C] M_PI not declared..?"
date: 2007-10-20
forum: Programming Talk
---

### Post by qscomputing on 2007-10-20
Hi there,

I'm just learning C but I do have a fair bit of experience with other languages, so I'm writing a few simple programs. I've written a simple program to do a for loop and a degrees to radians program:

```
#include <stdlib.h>
#include <stdio.h>
#include <math.h>

float deg2rad(float deg) {
  /* convert from degrees to radians */
  return (deg * (M_PI/180));
}

int main() {
  int lower=0, upper=0;
  printf("Please enter the lower limit: ");
  scanf("%d", &lower);
  printf("Please enter the upper limit: ");
  scanf("%d", &upper);

  printf("counting from %d to %d\n", lower, upper);
  
  for (int i=lower; i<=upper; i++) {
    float rad = deg2rad((float)i);
    printf("%d degrees = %f radians\n", i, rad);
  }
  return 0;
}
```

If I compile using gcc without any switches, I get an error telling me that I can't use a declaration in a for loop except in C99 mode, so I recompile with the switch -std=c99, and it informs me that M_PI isn't declared - even though it's a constant from the header. Removing the for loop and compiling without any switches works fine.

I want to leave the declaration of i in the for loop. If I define M_PI myself in the source file, it all works fine. Any ideas how to get the M_PI from math.h to work in C99 mode?

Thanks.

---

### Post by hod139 on 2007-10-20
I was curious about this, and I did a little searching.  Looks like they dropped M_PI in C99.  You can always define it yourself.

```

#ifndef M_PI
#define M_PI           3.14159265358979323846
#endif

```

---

### Post by slavik on 2007-10-20
have you tried linking against the math library? I just opened my /usr/include/math.h and M_PI is there ...

---

### Post by qscomputing on 2007-10-20
Yeah, I tried linking against the math library, and I checked in the header and the define is most definitely there.

---

### Post by maulattu on 2007-10-20
try to compile your program with the "-lm" directive, i.e.:
gcc -lm -o myprogram myprogram.c

It should work ;-)

---

### Post by hod139 on 2007-10-20
The problem, as the OP stated, is only when you use the C99 mode.
```

gcc -std=c99

```

And as I stated in my first post, the C99 standard dropped M_PI and gcc is abiding the standard.

---

### Post by qscomputing on 2007-10-20
Nope, still doesn't work. I really have no idea what's going on...

---

### Post by dwhitney67 on 2007-10-20
I did a little research concerning your question.  It appears that the powers-that-be at ISO felt that it was inappropriate to include M_PI (and other similar constants) in the standard C/C++.

Here's something I lifted from a web-page titled "[The GNU C Library - Mathematics]("http://www.sbin.org/doc/glibc/libc_19.html")":

[I][INDENT]...
The math library normally defines M_PI to a double approximation of pi. If strict ISO and/or POSIX compliance are requested this constant is not defined, but you can easily define it yourself:

#define M_PI 3.14159265358979323846264338327

You can also compute the value of pi with the expression acos (-1.0). 
...[/INDENT][/I]

---

### Post by wolfbone on 2007-10-20
gcc -std=gnu99 ...

or put #define _GNU_SOURCE at the top of your file and then use -std=c99.

---

### Post by qscomputing on 2007-10-21
That works fine; thanks very much for your help.

---

