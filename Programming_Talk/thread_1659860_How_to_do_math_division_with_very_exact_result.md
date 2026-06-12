---
title: "How to do math division with very exact result ?"
date: 2011-01-04
forum: Programming Talk
---

### Post by hakermania on 2011-01-04
how in this example will the result be very exact (e.g. if 10/3=3.333 and not 3)
```
if(a[i+n]/a[i]>kerd){
//do things
}
```
The thing is that for this occasion 11/3=10/3 and this destroys the whole program.

Thx for any answers :D

---

### Post by schauerlich on 2011-01-04
I'm assuming this is C? You can cast the numbers to doubles before you do the division.

```
if (a[i+n] / (double)a[i] > kerd)
```

---

### Post by MadCow108 on 2011-01-04
convert one (or both) to a double (or float)
if ((double)a/b ...)

---

### Post by worksofcraft on 2011-01-04
> **hakermania said:**
> how in this example will the result be very exact (e.g. if 10/3=3.333 and not 3)
```
if(a[i+n]/a[i]>kerd){
//do things
}
```
The thing is that for this occasion 11/3=10/3 and this destroys the whole program.

Thx for any answers :D

If you like to stay with integer arithmetic you might want to change it like so:

[php]
if(a[i+n]>kerd*a[i]){
//do things
}
[/php]
but beware if you can have negative numbers ;)

---

### Post by hakermania on 2011-01-04
> **worksofcraft said:**
> If you like to stay with integer arithmetic you might want to change it like so:

[php]
if(a[i+n]>kerd*a[i]){
//do things
}
[/php]but beware if you can have negative numbers ;)

Yeah, the thing is that I have negative numbers :/
Well the solution for my occasion (works properly) is:
```
f(float(a[i+n]/float(a[i]))>kerd){
//do things
}
```

---

### Post by Arndt on 2011-01-04
> **MadCow108 said:**
> convert one (or both) to a double (or float)
if ((double)a/b ...)

Doesn't this one first do a/b in integer and then convert to double?

---

### Post by Tony Flury on 2011-01-04
> **hakermania said:**
> how in this example will the result be very exact (e.g. if 10/3=3.333 and not 3)
```
if(a[i+n]/a[i]>kerd){
//do things
}
```
The thing is that for this occasion 11/3=10/3 and this destroys the whole program.

Thx for any answers :D

Just to be pendantic - 10/3 is not 3.333 it is 3.333333333333333333 (and so on for an infinite number of decimal places).

The only totally accurate way to represent some of the numbers is to use a rational notation (so 10/3 is reperesented as Integer-part 1, Numerator 1, Denominator 3) - but using rational numbers it means you can't be very accurate with numbers like pi, e etc - so in these cases floats and doubles might be better.

---

### Post by MadCow108 on 2011-01-04
> **Arndt said:**
> 
> 
if ((double)a/b ...)


Doesn't this one first do a/b in integer and then convert to double?

no conversions have higher precedence than all mathematical operators except postincrement.
Also it works left to right
[http://www.cppreference.com/wiki/language/operator_precedence](http://www.cppreference.com/wiki/language/operator_precedence)

---

### Post by JakeFrederix on 2011-01-05
The way doubles are stored makes it tricky to compare doubles with infinite digits.
In fact, the highest precision can only be reached when using numbers that are a power (or inverse power) of two, or a sum of such numbers.

If your program can tolerate it, work with a margin or error.
Instead of demanding "Are these equal?", You could try "Are they really close to eachother?"

---

### Post by nvteighen on 2011-01-06
The usual way to do this is to set an interval based equality. If this is C, use a function. If it's C++ you could create a class that overloads operator== to do the trick.

Assuming this is C because it will also be valid C++ in this case:
```

/* Compiled with flags:
 * -Wall -Wextra -pedantic -std=c99
 */

#include <stdio.h>

double double_abs(const double x)
{
    /* stdlib.h's abs() is for integers, not doubles... */

    return x >= 0 ? x : -1 * x;
}

int double_equal(const double x, const double y, const double e)
{
    /* Ok, this is horrible: if C had closures, I'd have used a
     * make_double_comparator procedure accepting the interval as argument and
     * returning a function that can be used as a comparator... *sighs*. 
     */

    return double_abs(x - y) <= e;
}

int main(void)
{
    double x = 1.0;
    double y = 3.0;
    double z = 0.333333;

    double quot = x / y;

    if(quot == z)
        (void)printf("%f == %f\n", quot, z);
    else
        (void)printf("%f != %f\n", quot, z);

    double e = 0.000001;
    if(double_equal(x / y, z, e))
        (void)printf("double_equal(%f, %f, %f) == 1\n", quot, z, e);
    else
        (void)printf("double_equal(%f, %f, %f) == 0\n", quot, z, e);

    return 0;
}

```

---

### Post by dwhitney67 on 2011-01-06
> **Tony Flury said:**
> Just to be pendantic - 10/3 is not 3.333 it is 3.333333333333333333 (and so on for an infinite number of decimal places).

Actually, if you are storing a 10 and a 3, and that is the limit of your precision, then the result of 10/3 would be 3, which is the best result you should "trust".

If you are dividing 10.00/3.00, then 3.33 would be appropriate.  Not every computer (and this includes the "El Cheapo" calculator) are made equal.  The computer's ability to store data is a major factor in determining the precision of a mathematical operation that one can trust.  The inputted data also is a factor; if you measure a particular distance using a yard-stick, and then you wish to divide that result by 3, your final result should be no more precise than what you could measure using your yard-stick.

---

### Post by trent.josephsen on 2011-01-06
> **nvteighen said:**
> 
```
double double_abs(const double x)
{
    /* stdlib.h's abs() is for integers, not doubles... */

    return x >= 0 ? x : -1 * x;
}
```

There's a better way.

[QUOTE=Linux Programmer's Manual]
NAME
       fabs, fabsf, fabsl - absolute value of floating-point number

SYNOPSIS
       #include <math.h>

       double fabs(double x);
       float fabsf(float x);
       long double fabsl(long double x);

       Link with -lm.
[/QUOTE]

---

### Post by nvteighen on 2011-01-06
> **trent.josephsen said:**
> There's a better way.

Which I didn't know. Thanks!

---

