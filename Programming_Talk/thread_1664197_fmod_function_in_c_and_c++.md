---
title: "fmod function in c and c++"
date: 2011-01-10
forum: Programming Talk
---

### Post by newport_j on 2011-01-10
I am trying to get a program to compile in both c and c++ and I am very close to success. It already compiles in c. The issue now is the function fmod. I list it below. As I said it compiles in c, but not in c++.
 
```

 
/*
* Copyright (c) 1989 The Regents of the University of California.
* All rights reserved.
*
* Redistribution and use in source and binary forms are permitted
* provided that: (1) source distributions retain this entire copyright
* notice and comment, and (2) distributions including binaries display
* the following acknowledgement: ``This product includes software
* developed by the University of California, Berkeley and its contributors''
* in the documentation or other materials provided with the distribution
* and in all advertising materials mentioning features or use of this
* software. Neither the name of the University nor the names of its
* contributors may be used to endorse or promote products derived
* from this software without specific prior written permission.
* THIS SOFTWARE IS PROVIDED ``AS IS'' AND WITHOUT ANY EXPRESS OR
* IMPLIED WARRANTIES, INCLUDING, WITHOUT LIMITATION, THE IMPLIED
* WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.
*/
#ifndef lint
static char sccsid[] = "@(#)fmod.c 5.2 (Berkeley) 6/1/90";
#endif /* not lint */
/* fmod.c
*
* SYNOPSIS
*
* #include <math.h>
* double fmod(double x, double y)
*
* DESCRIPTION
*
* The fmod function computes the floating-point remainder of x/y.
*
* RETURNS
*
* The fmod function returns the value x-i*y, for some integer i
* such that, if y is nonzero, the result has the same sign as x and
* magnitude less than the magnitude of y.
*
* On a VAX or CCI,
*
* fmod(x,0) traps/faults on floating-point divided-by-zero.
*
* On IEEE-754 conforming machines with "isnan()" primitive,
*
* fmod(x,0), fmod(INF,y) are invalid operations and NaN is returned.
*
*/
#if !defined(vax) && !defined(tahoe)
extern int isnan(),finite();
#endif /* !defined(vax) && !defined(tahoe) */
extern double frexp(),ldexp(),fabs();
#ifdef TEST_FMOD
static double
_fmod(x,y)
#else /* TEST_FMOD */
double
fmod(x,y)
#endif /* TEST_FMOD */
double x,y;
{
int ir,iy;
double r,w;
if (y == (double)0
#if !defined(vax) && !defined(tahoe) /* per "fmod" manual entry, SunOS 4.0 */
|| isnan(y) || !finite(x)
#endif /* !defined(vax) && !defined(tahoe) */
)
return (x*y)/(x*y);
r = fabs(x);
y = fabs(y);
(void)frexp(y,&iy);
while (r >= y) {
(void)frexp(r,&ir);
w = ldexp(y,ir-iy);
r -= w <= r ? w : w*(double)0.5;
}
return x >= (double)0 ? r : -r;
}
#ifdef TEST_FMOD
extern long random();
extern double fmod();
#define NTEST 10000
#define NCASES 3
static int nfail = 0;
static void
doit(x,y)
double x,y;
{
double ro = fmod(x,y),rn = _fmod(x,y);
if (ro != rn) {
(void)printf(" x = 0x%08.8x %08.8x (%24.16e)\n",x,x);
(void)printf(" y = 0x%08.8x %08.8x (%24.16e)\n",y,y);
(void)printf(" fmod = 0x%08.8x %08.8x (%24.16e)\n",ro,ro);
(void)printf("_fmod = 0x%08.8x %08.8x (%24.16e)\n",rn,rn);
(void)printf("\n");
}
}
main()
{
register int i,cases;
double x,y;
srandom(12345);
for (i = 0; i < NTEST; i++) {
x = (double)random();
y = (double)random();
for (cases = 0; cases < NCASES; cases++) {
switch (cases) {
case 0:
break;
case 1:
y = (double)1/y; break;
case 2:
x = (double)1/x; break;
default:
abort(); break;
}
doit(x,y);
doit(x,-y);
doit(-x,y);
doit(-x,-y);
}
}
if (nfail)
(void)printf("Number of failures: %d (out of a total of %d)\n",
nfail,NTEST*NCASES*4);
else
(void)printf("No discrepancies were found\n");
exit(0);
}
#endif /* TEST_FMOD */
 
 

```
 
The output of this file is
 
```

[FONT=Courier New][SIZE=3]srf_int2.c:107: error: call of overloaded ‘fmod(int&, int)’ is ambiguous[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]/usr/include/bits/mathcalls.h:188: note: candidates are: double fmod(double, double)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]/usr/include/c++/4.2/cmath:268: note:                 long double std::fmod(long double, long double)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]/usr/include/c++/4.2/cmath:264: note:                 float std::fmod(float, float)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]btm_int2.c: In function ‘void BTM_INT2(double, double, double, double*, double, double, double*, double, double, double, double*, double*, double*, double*, double*, double*, double*, int*, ENV_DEF*)’:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]btm_int2.c:129: error: call of overloaded ‘fmod(int&, int)’ is ambiguous[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]/usr/include/bits/mathcalls.h:188: note: candidates are: double fmod(double, double)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]/usr/include/c++/4.2/cmath:268: note:                 long double std::fmod(long double, long double)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]/usr/include/c++/4.2/cmath:264: note:                 float std::fmod(float, float)[/FONT][/SIZE]
 
 

```
 
 
 
 
There is no equivalent fmod in c so it compiles. Now when I try to compile in c++ with the g++ command, the output is as you see it above.
 
 
The functions that call fmod are now shown, but only the lines where fmod is called and used. 
 
```

if( fmod(ITER,2) != 0 && fabs(ZDEL1) > 0.0 ){
/*Use the secant method.*/
RRAYd = RRAY1 - ZDEL1*(RRAY2-RRAY1)/(ZDEL2-ZDEL1);
} else {
/*Use the bisection method.*/
RRAYd = 0.5*(RRAY1+RRAY2)

```
 
and 
 
```

if( fmod(ITER,2) != 0 && fabs(ZDEL1) > 0 ){
/*Use the secant method.*/
*RRAYd = RRAY1 - ZDEL1 * (RRAY2 - RRAY1) / (ZDEL2 - ZDEL1);
}else{
/*Use the bisection method.*/
*RRAYd = (RRAY1 + RRAY2) /2;

```
 
 
I believe that it is complaining because fmod is not prototyped. In c you do not have to prototype, but in c++ you must. 
 
 
However, there is something more at work here. In that c++, I think has an equivalent fmod, which is also named fmod. 
 
 
1. Now is it a good idea to redefine fmod like this or should I choose another name for my modular operation-say fmodd?
 
2. It does not like that I use integer variables. It gives three choices or candidates as it calls them. None of them are integer. I know that one can do modular arithmetic using real numbers, but what is wrong with using integers - it seems a logical, reasonable way to go? Yet it does not allow them.
 
Any help appreciated. Thanx in advance.
 
 
Newport_j

---

### Post by worksofcraft on 2011-01-10
I must admit I didn't work my way thru all of that... however,
The thing with fmod is:
```


     double fmod (      double numerator,      double denominator );
      float fmod (       float numerator,       float denominator );
long double fmod ( long double numerator, long double denominator );

```

so when you are passing integer parameters the poor compiler just doesn't know which one you would like to use !!!

My sugestion would be to cast the parameters explicity into one of the type catered for... my other suggestion would be to abandon attempts to mainatin C and C++ compatabilty. These languages are set on diverging courses and in time you are doomed to fail!

Personally I choose C++ and IMHO C should be frozen as an obsolete language... but I do understand that some might disagree with my POV :P

---

### Post by psusi on 2011-01-10
Where did you get that file and why are you trying to compile it?  It appears to be the bsd libc implementation of fmod.

---

### Post by Lootbox on 2011-01-10
worksofcraft is right; an int can be implicitly converted into any of those three types (float, double, long double), so a call that passes in an int is ambiguous. The appropriate call to the float version might look as follows:

```

fmod((float) ITER, 2.0f);

```

However, I also agree that you shouldn't concern yourself with compiler compatibility between C and C++. There are plenty of applications for which C is the language of choice, and plenty for which C++ is superior, but very rarely is the monster that is **C/C++** your friend.

As an example, if you decided to forego compatibility with C, you could take advantage of templates to reduce the need to write separate float, double, and long double versions of fmod.

---

### Post by MadCow108 on 2011-01-11
why not use the integer mod % when your arguments are integers?
e.g. a % 3

far saver than converting to float and hoping no rounding errors occur...
also its probably faster too

---

### Post by talonmies on 2011-01-11
> **newport_j said:**
> 
There is no equivalent fmod in c so it compiles. 

Wrong. There is an fmod function in the C standard library. The very code you are trying to compile is the BSD C standard library implementation of the C fmod function. That isn't why an error is being generated.

Look at the error message again:

```
rf_int2.c:107: error: call of overloaded fmod(int&, int) is ambiguous
```

There is a call to fmod in the code with integer arguments. A C compiler will probably complain about the implicit cast, but compile it anyway. A C++ compiler will not.

You should do two things

[LIST=1]
[*]Get rid of this fmod file, because you don't need it in either C or C++ (and it is a very poor implementation which will be bested in every way by the versions in modern C and C++ standard libraries)
[*]Fix the integer modulo call in the code to either use the integer modulo operator or use sane, explicit casting if that is really what is required (and I doubt that it is).
[/LIST]

---

### Post by newport_j on 2011-01-11
Doing the cast seemed to work. I do have a few questions.
 
1. Does this cast also work in c?
 
2. Why must one use the trailing f in 2.0 to make it 2.0f.
 
3. Since there is a fmod in c and c++, why did the compiler not complain when I redefined fmod? I would think that it would complain.
 
 
Newport_j

---

### Post by psusi on 2011-01-11
The compiler does not complain because you did not include math.h, and even if you did, it would not complain because you declared the same signature.  The linker will complain though, because you violate the one definition rule.

---

### Post by Lootbox on 2011-01-11
> Doing the cast seemed to work. I do have a few questions.
 
1. Does this cast also work in c?
If you use the (type) form of type casting, yes - some refer to it as a "C-style cast." C++ has its own type-casting system. Here, you would use static_cast<float>(x).

> 2. Why must one use the trailing f in 2.0 to make it 2.0f.
The trailing f specifies that the constant 2.0 should be treated as a float type, not as a double (which would happen if you left it off). This helps resolve any possible ambiguity between float and double. Here's an example:

```

#include <iostream>

using namespace std;

void foo(float lhs, float rhs)
{
    cout << "Float version!" << endl;
}

void foo(double lhs, double rhs)
{
    cout << "Double version!" << endl;
}

int main(int argc, char** argv)
{
    foo(2.0, 1.0f); // first argument is a double, second is a float
    return 0;
}

```

When I compile this with g++, I get the following warning (not an error, so it still compiles):

```
test.cpp:17: warning: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:
test.cpp:10: note: candidate 1: void foo(double, double)
test.cpp:5: note: candidate 2: void foo(float, float)
```

If you like to have warning-free code, then you should make sure these types of ambiguities don't pop up.

---

