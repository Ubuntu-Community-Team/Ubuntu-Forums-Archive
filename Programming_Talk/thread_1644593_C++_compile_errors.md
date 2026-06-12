---
title: "C++ compile errors"
date: 2010-12-13
forum: Programming Talk
---

### Post by newport_j on 2010-12-13
[FONT=Times New Roman][SIZE=3]*************network:~/Desktop/WEGtest$ [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]*************network:~/Desktop/WEGtest$ gcc -S fmod.c[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]*************network:~/Desktop/WEGtest$ g++ -S fmod.c[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fmod.c:60: error: ‘x’ was not declared in this scope[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fmod.c:60: error: ‘y’ was not declared in this scope[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fmod.c:60: error: initializer expression list treated as compound expression[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fmod.c:62: error: expected ‘,’ or ‘;’ before ‘double’[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fmod.c:63: error: expected unqualified-id before ‘{’ token[/SIZE][/FONT]
 
[FONT=Liberation Serif]*************network:~/Desktop/WEGtest$ [/FONT]

[FONT=Liberation Serif]I get the above output when I try to compile fmod.c in g++. it compiles perfectly when i compile it with gcc.[/FONT]

[FONT=Liberation Serif]I am not sure what the errors mean.[/FONT]


[FONT=Liberation Serif]The code is [/FONT]

```

 
[FONT=Liberation Serif]/*[/FONT]
[FONT=Liberation Serif]* Copyright (c) 1989 The Regents of the University of California.[/FONT]
[FONT=Liberation Serif]* All rights reserved.[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* Redistribution and use in source and binary forms are permitted[/FONT]
[FONT=Liberation Serif]* provided that: (1) source distributions retain this entire copyright[/FONT]
[FONT=Liberation Serif]* notice and comment, and (2) distributions including binaries display[/FONT]
[FONT=Liberation Serif]* the following acknowledgement: ``This product includes software[/FONT]
[FONT=Liberation Serif]* developed by the University of California, Berkeley and its contributors''[/FONT]
[FONT=Liberation Serif]* in the documentation or other materials provided with the distribution[/FONT]
[FONT=Liberation Serif]* and in all advertising materials mentioning features or use of this[/FONT]
[FONT=Liberation Serif]* software. Neither the name of the University nor the names of its[/FONT]
[FONT=Liberation Serif]* contributors may be used to endorse or promote products derived[/FONT]
[FONT=Liberation Serif]* from this software without specific prior written permission.[/FONT]
[FONT=Liberation Serif]* THIS SOFTWARE IS PROVIDED ``AS IS'' AND WITHOUT ANY EXPRESS OR[/FONT]
[FONT=Liberation Serif]* IMPLIED WARRANTIES, INCLUDING, WITHOUT LIMITATION, THE IMPLIED[/FONT]
[FONT=Liberation Serif]* WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.[/FONT]
[FONT=Liberation Serif]*/[/FONT]
[FONT=Liberation Serif]#ifndef lint[/FONT]
[FONT=Liberation Serif]static char sccsid[] = "@(#)fmod.c 5.2 (Berkeley) 6/1/90";[/FONT]
[FONT=Liberation Serif]#endif /* not lint */[/FONT]
[FONT=Liberation Serif]/* fmod.c[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* SYNOPSIS[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* #include <math.h>[/FONT]
[FONT=Liberation Serif]* double fmod(double x, double y)[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* DESCRIPTION[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* The fmod function computes the floating-point remainder of x/y.[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* RETURNS[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* The fmod function returns the value x-i*y, for some integer i[/FONT]
[FONT=Liberation Serif]* such that, if y is nonzero, the result has the same sign as x and[/FONT]
[FONT=Liberation Serif]* magnitude less than the magnitude of y.[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* On a VAX or CCI,[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* fmod(x,0) traps/faults on floating-point divided-by-zero.[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* On IEEE-754 conforming machines with "isnan()" primitive,[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]* fmod(x,0), fmod(INF,y) are invalid operations and NaN is returned.[/FONT]
[FONT=Liberation Serif]*[/FONT]
[FONT=Liberation Serif]*/[/FONT]
[FONT=Liberation Serif]#if !defined(vax) && !defined(tahoe)[/FONT]
[FONT=Liberation Serif]extern int isnan(),finite();[/FONT]
[FONT=Liberation Serif]#endif /* !defined(vax) && !defined(tahoe) */[/FONT]
[FONT=Liberation Serif]extern double frexp(),ldexp(),fabs();[/FONT]
[FONT=Liberation Serif]#ifdef TEST_FMOD[/FONT]
[FONT=Liberation Serif]static double[/FONT]
[FONT=Liberation Serif]_fmod(x,y)[/FONT]
[FONT=Liberation Serif]#else /* TEST_FMOD */[/FONT]
[FONT=Liberation Serif]double[/FONT]
[FONT=Liberation Serif]fmod(x,y)[/FONT]
[FONT=Liberation Serif]#endif /* TEST_FMOD */[/FONT]
[FONT=Liberation Serif]double x,y;[/FONT]
[FONT=Liberation Serif]{[/FONT]
[FONT=Liberation Serif]int ir,iy;[/FONT]
[FONT=Liberation Serif]double r,w;[/FONT]
[FONT=Liberation Serif]if (y == (double)0[/FONT]
[FONT=Liberation Serif]#if !defined(vax) && !defined(tahoe) /* per "fmod" manual entry, SunOS 4.0 */[/FONT]
[FONT=Liberation Serif]|| isnan(y) || !finite(x)[/FONT]
[FONT=Liberation Serif]#endif /* !defined(vax) && !defined(tahoe) */[/FONT]
[FONT=Liberation Serif])[/FONT]
[FONT=Liberation Serif]return (x*y)/(x*y);[/FONT]
[FONT=Liberation Serif]r = fabs(x);[/FONT]
[FONT=Liberation Serif]y = fabs(y);[/FONT]
[FONT=Liberation Serif](void)frexp(y,&iy);[/FONT]
[FONT=Liberation Serif]while (r >= y) {[/FONT]
[FONT=Liberation Serif](void)frexp(r,&ir);[/FONT]
[FONT=Liberation Serif]w = ldexp(y,ir-iy);[/FONT]
[FONT=Liberation Serif]r -= w <= r ? w : w*(double)0.5;[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]return x >= (double)0 ? r : -r;[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]#ifdef TEST_FMOD[/FONT]
[FONT=Liberation Serif]extern long random();[/FONT]
[FONT=Liberation Serif]extern double fmod();[/FONT]
[FONT=Liberation Serif]#define NTEST 10000[/FONT]
[FONT=Liberation Serif]#define NCASES 3[/FONT]
[FONT=Liberation Serif]static int nfail = 0;[/FONT]
[FONT=Liberation Serif]static void[/FONT]
[FONT=Liberation Serif]doit(x,y)[/FONT]
[FONT=Liberation Serif]double x,y;[/FONT]
[FONT=Liberation Serif]{[/FONT]
[FONT=Liberation Serif]double ro = fmod(x,y),rn = _fmod(x,y);[/FONT]
[FONT=Liberation Serif]if (ro != rn) {[/FONT]
[FONT=Liberation Serif](void)printf(" x = 0x%08.8x %08.8x (%24.16e)\n",x,x);[/FONT]
[FONT=Liberation Serif](void)printf(" y = 0x%08.8x %08.8x (%24.16e)\n",y,y);[/FONT]
[FONT=Liberation Serif](void)printf(" fmod = 0x%08.8x %08.8x (%24.16e)\n",ro,ro);[/FONT]
[FONT=Liberation Serif](void)printf("_fmod = 0x%08.8x %08.8x (%24.16e)\n",rn,rn);[/FONT]
[FONT=Liberation Serif](void)printf("\n");[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]main()[/FONT]
[FONT=Liberation Serif]{[/FONT]
[FONT=Liberation Serif]register int i,cases;[/FONT]
[FONT=Liberation Serif]double x,y;[/FONT]
[FONT=Liberation Serif]srandom(12345);[/FONT]
[FONT=Liberation Serif]for (i = 0; i < NTEST; i++) {[/FONT]
[FONT=Liberation Serif]x = (double)random();[/FONT]
[FONT=Liberation Serif]y = (double)random();[/FONT]
[FONT=Liberation Serif]for (cases = 0; cases < NCASES; cases++) {[/FONT]
[FONT=Liberation Serif]switch (cases) {[/FONT]
[FONT=Liberation Serif]case 0:[/FONT]
[FONT=Liberation Serif]break;[/FONT]
[FONT=Liberation Serif]case 1:[/FONT]
[FONT=Liberation Serif]y = (double)1/y; break;[/FONT]
[FONT=Liberation Serif]case 2:[/FONT]
[FONT=Liberation Serif]x = (double)1/x; break;[/FONT]
[FONT=Liberation Serif]default:[/FONT]
[FONT=Liberation Serif]abort(); break;[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]doit(x,y);[/FONT]
[FONT=Liberation Serif]doit(x,-y);[/FONT]
[FONT=Liberation Serif]doit(-x,y);[/FONT]
[FONT=Liberation Serif]doit(-x,-y);[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]if (nfail)[/FONT]
[FONT=Liberation Serif](void)printf("Number of failures: %d (out of a total of %d)\n",[/FONT]
[FONT=Liberation Serif]nfail,NTEST*NCASES*4);[/FONT]
[FONT=Liberation Serif]else[/FONT]
[FONT=Liberation Serif](void)printf("No discrepancies were found\n");[/FONT]
[FONT=Liberation Serif]exit(0);[/FONT]
[FONT=Liberation Serif]}[/FONT]
[FONT=Liberation Serif]#endif /* TEST_FMOD */[/FONT]
 

```
 
[FONT=Liberation Serif]Any help appreciated. Thanx in adavance.[/FONT]
 
[FONT=Liberation Serif]Newport_j[/FONT]

---

### Post by dwhitney67 on 2010-12-13
A function declaration such as the following is ok for C (but rarely used by anyone anymore), but AFAIK it was never accepted for the C++ standard.
```

void function(x,y)
  int x, y;
{
   ...
}

```
The correct syntax for C++ would be:
```

void function(int x, int y)
{
   ...
}

```

One has to question why you are attempting to compile C code using the "g++" compiler?  Did someone indicate to you that C and C++ were the same?  If they did, they were foolish to state that.

---

### Post by talonmies on 2010-12-13
It contains a K&R style function declaration which is illegal in C++.

Of course it begs the question why you are compiling an evil old BSD era fmod function when there is an implementation in the C++ standard library....

---

### Post by newport_j on 2010-12-13
It was not my choice to do this. I was given this legacy code to work with. It is incredibly complicated from a mathematical point of view. 
 
As they say years in the making.
 
It was written by engineers and mathematicians, not programmers, and it was written in c: the portable language. 
 
The analytical tools that i am using are writen for both c andf c++, but c is being phased out. 
 
So I think it wise to move it to c++.
 
That is all. We at this government facility have a lot of legacy code. The code is written in very outdated languages.
 
It would nice to have training in newer languages, but that is not about to happen with current budget shortfalls.
 
 
It does seem that popular literature still talks about c and c++ as if they are closely related.
 
Newport_j
 
 
Newport_j

---

### Post by talonmies on 2010-12-13
> **newport_j said:**
> 
It does seem that popular literature still talks about c and c++ as if they are closely related.
They are closely related. But they are not the same. And over time they have diverged considerably, especially in areas that were not in C at the time that C++ was developed and the Stroustrup book was published in the mid-eighties.

---

### Post by newport_j on 2010-12-13
I think I understand. I have to ask one question, though. The complex type in c was introduced in c99 to satisfy FORTRAN programmers transitioning to c.
 
Could someone elaborate on that? Everywhere I read about c99 and complex type I read this piece of info. What exactly happened here?
 
 
Newport_j

---

### Post by MadCow108 on 2010-12-13
fortran had COMPLEX, a complex number type needed often for e.g. scientific purposes.
C89 did not have this type.
So to help transition of fortran coders to C, C99 standardized a complex type for C too.
[http://www.gnu.org/s/libc/manual/html_node/Complex-Numbers.html](http://www.gnu.org/s/libc/manual/html_node/Complex-Numbers.html)

C++ also has a complex number type (in form of a class with overloaded operators):
[http://www.cplusplus.com/reference/std/complex/complex/](http://www.cplusplus.com/reference/std/complex/complex/)

---

### Post by Arndt on 2010-12-13
> **newport_j said:**
> It was not my choice to do this. I was given this legacy code to work with. It is incredibly complicated from a mathematical point of view. 
 
As they say years in the making.
 
It was written by engineers and mathematicians, not programmers, and it was written in c: the portable language. 
 
The analytical tools that i am using are writen for both c andf c++, but c is being phased out. 
 
So I think it wise to move it to c++.
 
That is all. We at this government facility have a lot of legacy code. The code is written in very outdated languages.
 
It would nice to have training in newer languages, but that is not about to happen with current budget shortfalls.
 
 
It does seem that popular literature still talks about c and c++ as if they are closely related.
 
Newport_j
 
 
Newport_j

If you have been given a large amount of legacy code written in C, you cannot phase out C. You may want to carefully adapt it to more modern C standards, in order to benefit from warnings and analysis tools. You have to decide yourself whether that is a good thing to do.

---

### Post by dwhitney67 on 2010-12-13
> **newport_j said:**
> It was not my choice to do this. I was given this legacy code to work with. It is incredibly complicated from a mathematical point of view. 
 
As they say years in the making.
 
It was written by engineers and mathematicians, not programmers, and it was written in c: the portable language. 
 
The analytical tools that i am using are writen for both c andf c++, but c is being phased out. 
 
So I think it wise to move it to c++.
 
That is all. We at this government facility have a lot of legacy code. The code is written in very outdated languages.
 
It would nice to have training in newer languages, but that is not about to happen with current budget shortfalls.
 
 
It does seem that popular literature still talks about c and c++ as if they are closely related.
 
Newport_j
 
 
Newport_j

I work on a gov't project also, and my task, along with 4 others, is to port C++, C, Java, csh, and perl, from a legacy system (Solaris 1.2) to RHEL 5.8.  All of us on the team are competent, and suited for the task.

You chided the original developers of your legacy code (which under certain circumstances is fine), but frankly you seem no better than they with your lack of experience.  Regardless, rather than whine about the hurdles you face, why don't you fix (ie port) the code versus just trying to fit a "square" into a "circle".

It may take you longer, and you may have battles with mgmt trying to define what term "porting" implies.  In your spare time, spend time going through a C++ book.  Write yourself little sample programs so that you become more comfortable with the C++ [STL]("http://www.cplusplus.com/reference/stl/").

Nobody gains "useful" experience by merely taking a C++ course; experience comes from programming, day-in/day-out, and learning from mistakes that you may make along your journey.

When you compile a C (or C++) module, and you encounter an error, the first thing is to go to the line where the compiler is complaining.  Examine the error, learn from it, and fix it.  Don't hesitate.  It doesn't matter that you find the perfect fix; it's gov't code that will probably not be used within 5 years.  And if you have the attitude that the gov't gets what it pays for, then you should not sweat a tear worrying about the failure of the program.

I used to work for the gov't, and now I work as a contractor (for the same agency).  I see many dumb decisions being made, many days in which resources (ie. people) are under-utilized, and where innovation is stifled because of some inherent fear to explore the unknown.  It makes me want to blow off my job, but damn it, I like the money.  So instead I just sit back, do the minimum required, and just shut my mouth.

---

### Post by talonmies on 2010-12-14
> **newport_j said:**
> 
The analytical tools that i am using are writen for both c andf c++, but c is being phased out. 
 
So I think it wise to move it to c++.

Isn't actually the case that this whole exercise is being driven solely by the desire to compile this code with Intel's C++ compiler which supports [Cilk Plus]("http://software.intel.com/en-us/articles/intel-cilk-plus/")? With the final objective of using that products compiler driven parallel programming primitives for performance improvement reasons?

---

### Post by newport_j on 2010-12-14
I am not chiding anybody for anything. The economics of this business requires an improvement in the code's execution speed. They gave it to me to check the math for improvments. I found none, all that could be done had been done. Then they said well why don't you try any other method you can think of and that is what I am doing. I get this assignment when work on other projects slows down. 
 
Many have tried, but no one has had any success. 
 
I would rather analyze it all in c and be done with it. I have taken courses in c++, but never programmed in it.
 
As a programmer I am a pretty good mathematican. If I can find what I need in c, I will. If it requires c++, then I will try to get it to c++ compile. 
 
If there is a c++ equivalent to fmod.c , please give me the link.
 
If you want an idea of the age of the code well it was originally in FORTRAN. 
 
Newport_j

---

### Post by Zugzwang on 2010-12-14
> **newport_j said:**
> 
If there is a c++ equivalent to fmod.c , please give me the link.


Huh? There's even a built-in function for "fmod" in the GNU compiler collection - just include "math.h". It will probably use the built-in function of your processor for this purpose. In any case, it will be better than the one you provided - both in terms of numerical stability and speed.

---

### Post by newport_j on 2010-12-14
Thanks for the advice. I will use it.
 
Newport_j

---

