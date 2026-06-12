---
title: "Very simple C question (maybe!)"
date: 2008-09-21
forum: Programming Talk
---

### Post by mdurham on 2008-09-21
Hi Guys, can anyone explain my problem as seen below. I'm Using Anjuta 2.4.1 to compile this simple C prog.
There appears to be a compiling problem using "sqrt(...)"
Could someone give it a try please.

Cheers, Mike

> #include <stdio.h>
#include <math.h>

double dosomething(double d)
{
[INDENT]return(d * d);[/INDENT]
}

int main()
{
[INDENT]	double d;

#if 0	// 1 == compile okay, 0 == NOT compile okay
	[INDENT]d = sqrt(16.0);[/INDENT]
#else
	[INDENT]d = dosomething(4.0);[/INDENT]
#endif
	d = sqrt(d);	// when ERROR: "main.c:18: undefined reference to `sqrt'"
	printf("\n%f", d);
	getchar();

	return (0);
[/INDENT]}


---

### Post by kknd on 2008-09-21
You need to link with the math library (gcc source.c -o app -lm )

---

### Post by John164918a on 2008-09-21
That seems really weird to me. I'm a bit of a noob though!

The code you've posted compiles perfectly with g++ but gives that error when compiled with gcc. Its interesting that the error you get is a linker error rather than a compiler one so maybe the sqrt function is defined in math.h but not in the equivalent .so file.

EDIT: Never mind, kknd just completely invalidated what I just said :-)

---

### Post by mdurham on 2008-09-21
> **kknd said:**
> You need to link with the math library (gcc source.c -o app -lm )

Thanks for the feedback, but why do I need to do that only if I compile with the #if 0? I still call sqrt() whether the #if is 0 or 1 and it works if it's set to 1.
Still puzzled!

As John164918a said, it compiles perfectly with G++

Cheers, Mike

---

### Post by kknd on 2008-09-21
> **mdurham said:**
> Thanks for the feedback, but why do I need to do that only if I compile with the #if 0? I still call sqrt() whether the #if is 0 or 1 and it works if it's set to 1.
Still puzzled!

As John164918a said, it compiles perfectly with G++

Cheers, Mike

here, because of the line "d = sqrt(d);" it will not compile (in fact it compiles, but doesn't find the symbol when linking with ld) in both ways, as expected.

---

### Post by mdurham on 2008-09-21
> **kknd said:**
> here, because of the line "d = sqrt(d);" it will not compile in both ways, as expected.

It does work if "#if 1" is set, try it!
What's wrong with d = sqrt(d)?
Seems a perfectly reasonable line of code to me.
Cheers, Mike

---

### Post by kknd on 2008-09-22
> **mdurham said:**
> It does work if "#if 1" is set, try it!
What's wrong with d = sqrt(d)?
Seems a perfectly reasonable line of code to me.
Cheers, Mike

The function sqrt is part of the library "libm.so", so if you call sqrt, you will need to link with this library ( -lm ).

Even if you change the macro th way you say, it will warn about the symbol not found (I've tried your code too).

---

### Post by nvteighen on 2008-09-22
> **John164918a said:**
> 
The code you've posted compiles perfectly with g++ but gives that error when compiled with gcc. Its interesting that the error you get is a linker error rather than a compiler one so maybe the sqrt function is defined in math.h but not in the equivalent .so file.


The reason why it works with g++ is because that compiler automatically links to the math library... but be careful, g++ is a C++ compiler and, even if it should be able to read C, better use the right compiler for each language (gcc for C).

---

### Post by mdurham on 2008-09-22
> **kknd said:**
> The function sqrt is part of the library "libm.so", so if you call sqrt, you will need to link with this library ( -lm ).

Even if you change the macro th way you say, it will warn about the symbol not found (I've tried your code too).

If I use "#if 1" It does work for me using Anjuta. It could be that Anjuta includes the math library if it finds sqrt(const), for some strange reason.

Thanks for the feedback, Mike

---

### Post by stroyan on 2008-09-23
The case that uses ```
d = sqrt(16.0);
```
is actually able to be reduced by the compiler to never calling sqrt().
The compiler assumes that the function is the standard math library
square root function.  It maps sqrt(16.0) to 4.0 at compile time.

The case that uses ```
d = dosomething(4.0);
```
is harder for the compiler to optimize.
The dosomething function may actually be supplied by a different
source file than your program depending on what other object files
are linked in and the link order.  So the compiler creates code
that actually calls dosomething and then calls sqrt.  I can
get the code using dosomething to link without libm if I change the
function declaration to ```
static double dosomething(double d)
```
and compile with "gcc -O2" so that the dosomething function is certain to
come from the same file and the optimization level is high enough to
inline the function into main.

---

### Post by mdurham on 2008-09-23
I've just tried it on Intrepid with Anjuta 2.4.2, whereas before I used Hardy with Anjuta 2.4.1. 
On Interpid it compiles both ways, no problems!

A note to stroyan.
The original problem was not to do with sqrt(16.0) or dosomething(), but with line 18: 
> d = sqrt(d); // when ERROR: "main.c:18: undefined reference to `sqrt'"

Thanks guys, Mike

---

### Post by stroyan on 2008-09-23
> **mdurham said:**
> I've just tried it on Intrepid with Anjuta 2.4.2, whereas before I used Hardy with Anjuta 2.4.1. 
On Interpid it compiles both ways, no problems!

A note to stroyan.
The original problem was not to do with sqrt(16.0) or dosomething(), but with line 18: 

The "d = sqrt(d)" in line 18 is just one more iteration of constant evaluation.
If the compiler can reduce the previous assignments to d into a constant,
then it can replace the sqrt and assignment in line 18 with a constant.
If the value of d before line 18 is potentially variable then the compiler
needs to really use a function call to sqrt.

---

### Post by mdurham on 2008-09-23
> **stroyan said:**
> The "d = sqrt(d)" in line 18 is just one more iteration of constant evaluation.
If the compiler can reduce the previous assignments to d into a constant,
then it can replace the sqrt and assignment in line 18 with a constant.
If the value of d before line 18 is potentially variable then the compiler
needs to really use a function call to sqrt.

I think that explains it perfectly. But it's interesting that it works without additional instructions (ie including the maths lib) on Intrepid.
Cheers, Mike

---

### Post by sajithn on 2010-02-28
When you just use sqrt(16.0) you might not need to link with libm.so (-lm option). This is because sqrt() is a built-in function of gcc (on my machine gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3) and when you call sqrt with a constant, it simply uses the built-in function sqrt.

You can disable all built-in functions with -fno-builtin option of gcc, or  specifically in the case of sqrt with the option -fno-builtin-sqrt.
Then it does complain about "undefined reference to `sqrt'". If we use either of these options, we need to link with -lm to resolve the symbol sqrt.

But when you use a variable for invoking sqrt, gcc does not use any built-in function. It tries to call the function sqrt, which is typically defined in libm.so forcing us to use -lm always.

Hope this clarifies the issue.

---

### Post by nvteighen on 2010-02-28
> **sajithn said:**
> When you just use sqrt(16.0) you might not need to link with libm.so (-lm option). This is because sqrt() is a built-in function of gcc (on my machine gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3) and when you call sqrt with a constant, it simply uses the built-in function sqrt.

You can disable all built-in functions with -fno-builtin option of gcc, or  specifically in the case of sqrt with the option -fno-builtin-sqrt.
Then it does complain about "undefined reference to `sqrt'". If we use either of these options, we need to link with -lm to resolve the symbol sqrt.

But when you use a variable for invoking sqrt, gcc does not use any built-in function. It tries to call the function sqrt, which is typically defined in libm.so forcing us to use -lm always.

Hope this clarifies the issue.

Ugh... You're responding to a 1.5 years old thread...

Actually, the thing is that when he compiled with g++, it worked because g++ links your program with libm.so by default. gcc doesn't.

---

