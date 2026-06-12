---
title: "Where are the trig declarations?"
date: 2013-10-22
forum: Packaging and Compiling Programs
---

### Post by baruch60610 on 2013-10-22
I'm trying to write a C program containing a few trig founctions - sin, cos, nothing too serious.  I #include <math.h>, I link using -lm, but I get errors like: "undefined reference to 'sin'".  Sure enough, <math.h> has no declaration for sin or any other trig function.

When I check the mandev pages I am told that (and I quote between the asterisks):

************************
NAME

cos, cosf, cosl - cosine function
SYNOPSIS

#include <math.h> 

double cos(double x);

float cosf(float x);


long double cosl(long double x);


Link with -lm. 
************************

So, OK, I need to #include <math.h>, and link with -lm, which is what I'm doing.  Where does the declaration for cos  live?  As far as I can see, the documentation is incorrect, which I find hard to believe.  What am I missing?

Anyone know what I need to do so I can write the next killer app that does cosines?

-B

---

### Post by steeldriver on 2013-10-22
Are you using gcc? If so what is your actual gcc command line? 

You are probably linking the math library in the wrong place - for the current gcc compiler it needs to go AFTER the C source that calls it i.e.

```
gcc -o *yourprog yoursource.c* -lm
```

i.e. references resolve from left to right, NOT

```
gcc -o *yourprog *-lm *yoursource.c*
```

FYI it's important to understand he difference between **declarations **(in header files) and **definitions **(or in your case ***undefined** **references***)

---

### Post by baruch60610 on 2013-10-22
Steeldriver, thanks for your input.  I'm almost certain I've got the -lm in the wrong place.  I'll check it out when I get a chance, and post a "solved" if that's the problem.

I wasn't clear about the distinction between declarations and definitions.  I mean, I know the difference, but... are you saying that the problem is in the library (or the compiler/linker not being able to find the library)?

Anyway, thanks for your help.

-B

---

### Post by baruch60610 on 2013-12-19
Thanks, Steeldriver, for your tip.  I just had the -lm in the wrong place.  Somehow I interpreted the ld man page to mean these things needed to precede the source.  It doesn't *say* that, but that's how I interpreted it.

Anyway, thanks to your input, I'm happily going along making other mistakes.  Thanks.

-B

---

