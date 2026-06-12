---
title: "Help compiling a conditional statement in C?"
date: 2011-04-09
forum: Programming Talk
---

### Post by VonFuzzball on 2011-04-09
I've just recently started learning C programming, and I'm trying to create a program that asks for an angle theta, in radians, from the user and then reports either the value of sin(theta) or cos(theta), depending on which one has the smaller absolute value.

My code is this:

```
#include <stdio.h>
#include <math.h>

int main (void)
{
double angle, angle2, theta;

printf("Enter the angle, theta, in radians:");
scanf("%lf",&theta);

angle = sin(theta);
angle2 = cos(theta);

if (angle < angle2) 
      { printf("Value of sin(theta) is %g"); }
else
      { printf ("Value of cos(theta) is %g"); }
}
```The program will compile and run, but it doesn't do what I want it to. As a matter of fact, it returns the same incorrect number regardless of what value I enter for the angle. Any help would be appreciated!

---

### Post by GeneralZod on 2011-04-09
Your last two printf's specify how to format the values, but not the values themselves :)

---

### Post by VonFuzzball on 2011-04-09
Oh, of course! Thanks for pointing that out.

Now it works perfectly if the input is angle in degrees. But if you enter angles in radians, the output is still a little funky. Hm.

But anyway, thanks again! (:

---

### Post by JupiterV2 on 2011-04-11
1) Make sure when you're compiling your program to turn on warnings. At a minimum, assuming you're using GCC, use -Wall. The level provided by -Wall would have warned you that you were missing an argument to printf().

2) You may find using a precision specifier useful for giving proper output. printf("%.3g") would truncate the result to 3 decimal points.

3) If you want the absolute value of your input, don't you want to use abs() on theta before getting the sine or cosine of the angle?

---

