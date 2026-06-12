---
title: "Crippled math.h?"
date: 2007-01-30
forum: Programming Talk
---

### Post by tdlrali on 2007-01-30
Hey Community!

I have a problem with the math functions (math.h) in C. Check out the following code:

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define PI 3.14159265

int main() {
        printf("X: %u, Y: %u: %f degrees",20,50,atan2(50.0,20.0) * 180.0 / PI);
        return 0;
}

```

Error returned:
```

/tmp/ccU00Hbo.o: In function `main':
drive.c:(.text+0x25): undefined reference to `atan2'
collect2: ld returned 1 exit status

```

This is the first time that I am programming under Linux, I never had a problem with code like this before under Windows. Also, I am 99.99% sure that atan2 is in math.h.

Am I missing any packages? I have build-essentials.

Thank you!

---

### Post by Wybiral on 2007-01-30
Have you tried compiling it with the "-lm" flag?

---

### Post by tdlrali on 2007-01-30
wow, thanks! that worked :)

so what does that flag do?
-l for libraries?
what does -m do?

---

### Post by Wybiral on 2007-01-30
Yes, "-lm" links to the math library.

---

### Post by amo-ej1 on 2007-01-31
In case you wonder where this come from:


man atan2: 

```

ATAN2(3)                   Linux Programmer’s Manual                  ATAN2(3)

NAME
       atan2, atan2f, atan2l - arc tangent function of two variables

SYNOPSIS
       #include <math.h>

       double atan2(double y, double x);
       float atan2f(float y, float x);
       long double atan2l(long double y, long double x);

       Link with -lm.


```

---

