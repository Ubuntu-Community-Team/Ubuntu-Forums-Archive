---
title: "Getting math functions to work in C"
date: 2013-08-18
forum: Programming Talk
---

### Post by seriouslylinux on 2013-08-18
I am using GCC on Ubuntu 12.10.  I am trying to use math functions; specifically sqrt().  When I use a line of code that has a constant in it "sqrt(4)" the function compiles and gives me the right answer in the terminal.  When I use a variable "sqrt(number)" the compiler returns with "undefined reference to `sqrt'".  I believe I need to use the linker to a math library since I encountered this same problem with Netbeans.  I do not know and am not able to find the name of the library or file that would solve this problem.  I have tried "-std=iso9899:1990" since that std requires only <math.h> and I still get the same error message.  Here is the snippet of code from the program:
double number;
    
    printf ("Enter a number: ");
    scanf("%lf", &number);
    printf ("The sqrt of 4 is: %lf\n", sqrt(4));
    printf ("The sqrt of your number is: %lf\n", sqrt(number));

---

### Post by steeldriver on 2013-08-18
The library is libm, it may be specified on the gcc command line as -lm e.g.

```
gcc -o yourprog yourprog.c -lm
```

---

### Post by spjackson on 2013-08-19
> **seriouslylinux said:**
> I believe I need to use the linker to a math library since I encountered this same problem with Netbeans.  I do not know and am not able to find the name of the library or file that would solve this problem.
steeldriver has given the right answer, but I wonder, did you try "man sqrt"? In the synopsis, it says "Link with -lm."

---

### Post by seriouslylinux on 2013-08-28
Thank you for the info and the replies. The math functions are working.

---

