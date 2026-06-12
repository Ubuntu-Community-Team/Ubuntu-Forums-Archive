---
title: "factoring integers"
date: 2009-02-22
forum: Programming Talk
---

### Post by Marko A on 2009-02-22
I'm working on a factoring program.

if I try to factor;

50345718910157733433 (20 digits)

I get an incorrect result, yet if I multiply out the factors the program gives I get this back;

50345718910157733888

notice it's only off in the last 3 digits.

I suspect a precision problem.

I'm doing this in C using the types 'long long' and 'long double'.

What would be an easy (hopefully) way to get better precision?

The program factors correct if I try numbers up to 16 digits, after that it goes wrong.

I think my program would still work for larger numbers if only I could hold larger numbers in memory it'd probably work to larger integers.

---

### Post by PythonPower on 2009-02-22
Post code and I'll help you better...

I would try to avoid using doubles at all if you're factoring integers. I imagine they occur because of using the sqrt() function in math.h but there are special techniques one should use if they go down that route.

---

### Post by croto on 2009-02-22
First of all I totally agree with previous poster: floating point representation is a big no for the problem you want to solve. Besides that, I think you may be pushing the limits of "long long", which can represent up to 20 decimal digits (from 0 to 18,446,744,073,709,551,615). You may want to consider to use infinite/arbitrary precision integer types. There are libraries available for C, but I wouldn't know which one to recommend because I haven't used any. On the other hand, I know that Python has built-in support for infinite precision arithmetic.

---

### Post by Marko A on 2009-02-22
> **croto said:**
> First of all I totally agree with previous poster: floating point representation is a big no for the problem you want to solve.



One of the reasons I used floating point was to be able to represent bigger numbers.


> **PythonPower said:**
>  I imagine they occur because of using the sqrt() function in math.h but there are special techniques one should use if they go down that route.


yes, that was another reason.
I replaced all the floating point types with integer types.  The program still works, but the precision problem is still there.

> **croto said:**
> 
You may want to consider to use infinite/arbitrary precision integer types.



Agreed,  I found this library [http://http://www.tc.umn.edu/~ringx004/mapm-main.html]("http://http://www.tc.umn.edu/~ringx004/mapm-main.html") and I'll be studying it.  I need the bigger integer types.


Thanks all.;)

---

### Post by PythonPower on 2009-02-24
I'd check out [GMP]("http://gmplib.org/") if you want large integers.

---

### Post by monkeyking on 2009-02-24
yes, use gmp.

---

