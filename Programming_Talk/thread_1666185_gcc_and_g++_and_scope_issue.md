---
title: "gcc and g++ and scope issue"
date: 2011-01-13
forum: Programming Talk
---

### Post by newport_j on 2011-01-13
```

/*! \file zbrlael.c
\brief determine complex reflection coefficient
\par 
Applied Physics Laboratory, University of Washington
\par
Add shear-supporting sediment for reflection loss
\par
High Frequency Ocean Environmental Acoustic models
\par
frequency range 10-100 khz
\par
this code module was developed by the Applied Physics Laboratory,
University of Washington, to replace HFEVA bottom loss algorithms
\par
Developed in MATLAB by Darrell R. Jackson
\par
Ported to FORTRAN by KY Moravan 2/2004
\par
Program to determine complex
reflection coefficient vs. rho, nu, delta, nut, deltat.
The environment consists of a semi-infinite water
overlying a semi-infinite elastic layer. The water is layer 1,
layer 2 is the one whose parameters are varied.
\par
(L. M. Brekhovskikh and O.A. Godin, "Acoustics of Layered Media I, 
Plane and Qua si-Plane Waves," Springer-Verlag, Heidelberg, 1990, p. 94. )
(Hamilton, Geophysics, Vol 37, N0 4, August, 1972, p621.)
\par
\author Darrell R. Jackson
\author KY Moravan
*/
#include <math.h>
#include "math-complex.h"
#include <stdio.h>
#include "SIMdefines.h"
#include "WAFmathBase.h"
#include "envstructdefs.h"
#include "ModsFunDefs.h"
/*!\brief
determine complex reflection coefficient
\par
water/elastic-sediment reflection loss in intensity,
brlael is set to 1 for grazing angles less than 0.015
degree to avoid singularity and using double precision.
\par
\param ang grazing angle (deg)
\param nu compressional wave speed ratio,(dimensionless)
\param delta loss parameter,compressional
\param nut shear wave speed ratio(dimensionless)
\param deltat loss parameter,shear
\param rho density ratio,(dimensionless)
\return water/elastic-sediment reflection loss in intensity.
\par
\note
Use only within the angular range of 0.0 to 90 degrees
\note
the acoustic frequency and the water sound speed at the
water/sediment are not explicitly shown in this program, as
these two quantities were cancelled out in the loss expression
*/
double brlael(double ang, double nu, double delta ,double nut, double deltat, double rho){
 
double_complex al,at,kl,kt,ref,temp;
double brlael,thetar,kti,omega,kx,kw,cl,ct;
 
omega = 2.0*M_PI;
kw = omega;
cl=nu;
ct=nut;
 
al = omega/cl;
kl = al * (1.0 + -delta*I);
 
at = omega/ct;
kt = at * (1.0 + -deltat*I);
 
if (ang < 0.015){
brlael = 1.0;
} else {
thetar = M_PI*ang/180.0;
kx = kw*cos(thetar);
kti = fabs(kx);
ref = gam(kti,kw,kl,kt,rho);
temp = ref * conj(ref);
brlael = creal(temp);
};
return(brlael); 
}

``` 
 
The above code compiles with no errors in gcc as part of a bigger program, but when it compiles with g++, the output is as seen below.
 
 
[FONT=Times New Roman][SIZE=3]~/Desktop/WEGtestcpp$ gcc -m32 -lm -lrt -g zbrlael.c[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In file included from zbrlael.c:37:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]WAFmathBase.h:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘LOGICAL’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In file included from zbrlael.c:39:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ModsFunDefs.h:28: error: expected ‘)’ before ‘DEBUG’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ModsFunDefs.h:31: error: expected ‘)’ before ‘DEBUG’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ModsFunDefs.h:35: error: expected ‘)’ before ‘DEBUG’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ModsFunDefs.h:38: error: expected ‘)’ before ‘DEBUG’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]james ~/Desktop/WEGtestcpp$ g++ -m32 -lm -lrt -g zbrlael.c[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]zbrlael.c: In function ‘double brlael(double, double, double, double, double, double)’:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]zbrlael.c:74: error: ‘I’ was not declared in this scope[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]zbrlael.c:87: error: ‘creal’ was not declared in this scope[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]james ~/Desktop/WEGtestcpp$ [/SIZE][/FONT]
 
 
 
I am only concerned with the errors: I and creal was not declared in this scope. This code I would think would compile under gcc and g++, but it gives these errors when compiling with g++.
 
Why does the c compiler not mind that I and creal are not declared in scope, but the c++ compiler does mind?
 
 
Any help appreciated. Thanx in advance.
 
Newport_j

---

### Post by dwhitney67 on 2011-01-13
When you compiled with 'gcc', you got errors too.  What's the deal?  As for the errors with "g++", those once again seem related to the "complex" type.

Either way, the error seems to be complaining about an issues within these two header files:
```

#include "envstructdefs.h"
#include "ModsFunDefs.h"

```

Btw, it is good practice to include project header files before including system header files, such as stdio.h.  Consider reorganizing the ordering of your include statements.

---

### Post by newport_j on 2011-01-13
I meant to say that zbrlael.c compiles in a complete program flawlessly usng gcc. It does not give any errors. For this posting I just tried to compile only the function zbrlael.c. It did give additional errors, but I can make them disappear when I compile the collection of files.
 
The g++ compile of the complete program only gave these two errors that I outlined above for zbrlael.c - the variables being out of scope. My program has several other functions thta give similar errors when it compiles with g++. It gives no such errors when compiles with gcc.
 
I will post the output from the complete compilation.
 
Here is the output when I compile with g++, again no errors when I compile with gcc.
 
```

[FONT=Courier New][SIZE=3]lwr_vtx2.c: In function ‘void LWR_VTX2(double, double*, double*, double*, double*, int*, ENV_DEF*)’:[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]lwr_vtx2.c:83: error: ‘cabs’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbtms94.c: In function ‘double BTMS94(LOGICAL, double, double, double, double, double, double, double, double, double, int*)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbtms94.c:216: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbtms94.c:227: error: ‘cabs’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]chn_rfl2.c: In function ‘void CHN_RFL2(double*, int, double*, double*, double, int, double_complex*)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]chn_rfl2.c:115: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]chn_rfl2.c:131: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]chn_rfl2.c:157: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zblos94.c: In function ‘double BLOS94(double, double, double, double)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zblos94.c:100: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zblos94.c:103: error: ‘csqrt’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zblos94.c:114: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c: In function ‘double SIGMPR(LOGICAL, double, double, double, double_complex, double, double)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:70: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:70: error: ‘cimag’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:91: error: ‘csqrt’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:105: error: cannot convert ‘std::complex<double>’ to ‘double’ in assignment[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:109: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpr.c:109: error: ‘cimag’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c: In function ‘double SIGMPV(LOGICAL, double, double, double_complex, double, double, double)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c:68: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c:68: error: ‘cimag’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c:87: error: ‘csqrt’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c:101: error: ‘cimag’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zsigmpv.c:104: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbrlael.c: In function ‘double brlael(double, double, double, double, double, double)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbrlael.c:74: error: ‘I’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbrlael.c:87: error: ‘creal’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbeta.c: In function ‘double_complex beta(double, double_complex)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbeta.c:29: error: ‘csqrt’ was not declared in this scope[/FONT][/SIZE]

```
 
As you can see this error pops frequently when I compile the complete program in g++. In fact it is the only error, but is occurs many times. The program compiles perfectly when I compile it with gcc. 
 
I am assuming that there is a scope issue here. If I fix it for one function, then I can fix it for all of them.
 
The point is how or what do I fix? 
 
This is a scope issue. What to do to fix it?
 
Any help appreciated. Thanx in advance.
 
 
Newport_j

---

### Post by talonmies on 2011-01-13
There is no scope errors reported in what you have posted. Every error is because of undefined C99 complex library functions.

The C++ standard library complex functions are listed [here]("http://www.cplusplus.com/reference/std/complex/"). You will have to do something about defined those C99 calls in terms of C++ versions, or change the code to use the correct C++ versions.

---

### Post by Vox754 on 2011-01-13
> **newport_j said:**
> ...
 
Here is the output when I compile with g++, again no errors when I compile with gcc.
...


I don't care about your problems trying to compile a program as both C and C++. It's just crazy either way.

I am only irked that every time you post code in this forum
1. You randomly change the font and size of the code
2. You sometimes use "code" tags and sometimes you don't
3. You don't indent your code

Example. Code in "code" tags, but without indentation.
```

if (ang < 0.015){
brlael = 1.0;
} else {
thetar = M_PI*ang/180.0;
kx = kw*cos(thetar);
kti = fabs(kx);
ref = gam(kti,kw,kl,kt,rho);
temp = ref * conj(ref);
brlael = creal(temp);
};
return(brlael); 
}

```

Example. Code in "code" tags, but font and size changes.
```

[FONT=Courier New][SIZE=3]lwr_vtx2.c: In function ‘void LWR_VTX2(double, double*, double*, double*, double*, int*, ENV_DEF*)’:[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]lwr_vtx2.c:83: error: ‘cabs’ was not declared in this scope[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]zbtms94.c: In function ‘double BTMS94(LOGICAL, double, double, double, double, double, double, double, double, double, int*)’:[/FONT][/SIZE]

```
 
Example. Code without "code" tags, with font and size changes. Times?! Why Times?!
[FONT=Times New Roman][SIZE=3]~/Desktop/WEGtestcpp$ gcc -m32 -lm -lrt -g zbrlael.c[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In file included from zbrlael.c:37:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]WAFmathBase.h:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘LOGICAL’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]In file included from zbrlael.c:39:[/SIZE][/FONT]

Why do you do this? Why? WHY???
It's driving me crazy!
Do you write your code in Microsoft Word, and then paste it in the forum?

Copy the code from your text file, and paste it like it is inside "code" tags. Same with the terminal output. Is that so difficult?
```

~/Desktop/WEGtestcpp$ gcc -m32 -lm -lrt -g zbrlael.c
In file included from zbrlael.c:37:
WAFmathBase.h:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘LOGICAL’
In file included from zbrlael.c:39:

lwr_vtx2.c: In function ‘void LWR_VTX2(double, double*, double*, double*, double*, int*, ENV_DEF*)’:
lwr_vtx2.c:83: error: ‘cabs’ was not declared in this scope
zbtms94.c: In function ‘double BTMS94(LOGICAL, double, double, double, double, double, double, double, double, double, int*)’:

```

The code tags use a monospaced font, and preserves any spaces and indentation, which makes the code look pretty and readable.

Don't make font changes. Just use "code" tags. Simple!

---

### Post by Vox754 on 2011-01-13
...

---

### Post by MadCow108 on 2011-01-13
I'd say its slowly time to ask your boss to assign you to a different project which you are actually capable of doing.
I don't see how your are ever going to succeed with your (pointless) plan when you have no clue about the languages involved ...

---

### Post by dwhitney67 on 2011-01-13
> **newport_j said:**
> 
Any help appreciated. Thanx in advance.


Did you decide to go down the path of using an #ifdef __cplusplus (sp?) to determine how to define double_complex when using the C vs. C++ compiler?  If so, then you are going to have to do something similar in each C module that uses the double_complex.

For example:
```

void someFunction(double_complex* c)
{
#ifdef __cplusplus

       // new code that YOU must develop!
#else

       /* original C code */

#endif
}

```
Porting s/w sucks... better get used to it.

---

### Post by nvteighen on 2011-01-13
After reading several of your threads, I'm really curious about what you're really doing with all of this. For instance, I warn you that this code you posted is copyrighted and you should ask for permission to post it here.

I think you assume that any piece of code should be automatically compilable by both C and C++ compilers because C and C++ look similar or are compatible to some extent. No: they are different languages and making C code work as C++ (or viceversa) needs special configuration measures.

So, what is this all about?

---

### Post by Lootbox on 2011-01-13
> **dwhitney67 said:**
> Btw, it is good practice to include project header files before including system header files, such as stdio.h.  Consider reorganizing the ordering of your include statements.

Sorry this somewhat off-topic, but out of curiosity, is there a particular reason that's the case? Or is it just standard practice?

---

### Post by MadCow108 on 2011-01-13
it helps detecting missing system includes. e.g.
```

// myfile.h
#include <string>
#include <otherfile.h>

```
when otherfile.h now uses string but does _not_ include the header for it will remain undetected when myfile.h is included before otherfile.h and it will breaks when someone reverses the order

---

