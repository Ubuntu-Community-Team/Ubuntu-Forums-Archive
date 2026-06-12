---
title: "Is this a glibc underflow bug?"
date: 2007-08-10
forum: Programming Talk
---

### Post by hlmuller on 2007-08-10
**[COLOR="Blue"]Issue Description:[/COLOR]**

I bumped into this while learning the C language with "C Primer Plus" in the 3d chapter exercises.  Part of the first exercise is to develop a program that identifies what your system does with floating point underflow.  FLT_MIN identifies the smallest valid float value.  Dividing that number by two should create a floating point underflow condition.  It does not, but dividing by 20, does.  The code below is what I developed to demonstrate that part of the exercise:

```
/* underflow.c -- floating point underflow */
/* The -lm switch has to be used with gcc to build this */

#include <stdio.h>
#include <float.h>
#include <fenv.h>

int main(void)
{
	feclearexcept(FE_ALL_EXCEPT);
	
	float flt_min = FLT_MIN;
	float underflow = flt_min / 2.0e+1;
	int test = fetestexcept(FE_UNDERFLOW);
	
	printf("\nThe smallest float value that can be used on this machine is: ");
	printf("%e\n", flt_min);
	printf("%e / 2 = %e\n\n", flt_min, underflow);
	if (test)
	{
		printf("The floating point underflow exception flag is set.\n\n");
	}

	return 0;
}

```

**[COLOR="Blue"]Question:[/COLOR]**

Is this a glibc bug, or is there a subtlety I don't understand?  Thanks for any input!

Harv

---

### Post by Soybean on 2007-08-10
I don't know... would you really say that *not* triggering an underflow error in a particular situation is a "bug?" ;)

As for what's actually going on there... FLT_MIN isn't the smallest representable float, obviously. It's the smallest "normalized" floating point value... I *think* it would be accurate to say that it's the smallest floating point value that can be represented at the maximum precision level of a float.

Basically, I *believe* that FLT_MIN/2.0 has fewer digits than FLT_MIN, or at least, fewer digits in its binary representation. So in that sense, it's a "less precise" number, and is easier to represent than FLT_MIN. I think you'll find that you can divide FLT_MIN by larger powers of 2 without an underflow, as well, while dividing by 2.1 or 1.9 *will* trigger an underflow.

It's one of those wild and crazy floating-point things where I'm a little fuzzy on the details, but does that help at all? You could probably check out the wiki article on the floating point standard if you wanted to get a bit more in-depth: [http://en.wikipedia.org/wiki/IEEE_floating-point_standard](http://en.wikipedia.org/wiki/IEEE_floating-point_standard)

---

### Post by hlmuller on 2007-08-10
Thanks for the response.  For the past 3 days, I've researched the issue from many different sources:[LIST]
[*]c99 standard
[*]glibc manual
[*]google
[*]etc.
[/LIST]

Based on that research, attempting to produce anything smaller than FLT_MIN, should set the FE_UNDERFLOW flag.  

Unless someone can explain why dividing the FLT_MIN value by 2 doesn't set the FE_UNDERFLOW flag, but dividing by 20 does, then I am inclined  to believe there is a bug in the glibc implementation.

This provides a great hands-on tutorial for floating point numbers:  [http://www.cs.utah.edu/~zachary/isp/applets/FP/FP.html]("http://www.cs.utah.edu/~zachary/isp/applets/FP/FP.html")

---

### Post by Soybean on 2007-08-10
Well... you don't have to believe me, but I'm pretty confident it's not a bug. Also, it's not in glibc. The underflow error flag is set by the processor -- it's a very low-level thing. 

Underflow and overflow errors are only triggered when the processor tries to do some arithmetic, but the result won't fit in the register; that is, it only happens if information is lost. FLT_MIN/2 can be accurately represented in a 32-bit float, so calculating it doesn't set the underflow flag. 

To demonstrate that no information is lost when dividing by 2, note that 
```

((FLT_MIN / 2.0) * 2.0) == FLT_MIN

```

Why, exactly, do you think it *ought* to set the underflow flag? I suspect you're either misinterpreting what FLT_MIN is (to be fair, I'm not helping there, since I don't really know how it's defined), or you misunderstand what an underflow error is.

---

### Post by hlmuller on 2007-08-10
soybean,

First, I appreciate your input on an issue that is relatively unimportant in the context of life.

I agree that there is most likely a misinterpretation I am making, and that the 'bug' is in my wetware between my ears.

My understanding of FLT_MIN may be the issue.  I understand FLT_MIN is supposed to represent the smallest number representable by the hardware (for the single precision floating point type).  In fact, the value of FLT_MIN on my system = the approximate value indicated in Intel's architecture book. By my understanding of the term underflow, attempting to represent a number smaller than FLT_MIN ( otherwise denormal), should set the underflow exception flag.

Feel free to continue making suggestions, I confess I still do not grok why 20 sets the exception flag, but 2 doesn't.

Harv

---

### Post by aks44 on 2007-08-10
> **Soybean said:**
> Underflow and overflow errors are only triggered when the processor tries to do some arithmetic, but the result won't fit in the register

> **hlmuller said:**
> Feel free to continue making suggestions, I confess I still do not grok why 20 sets the exception flag, but 2 doesn't.

I may well be wrong on this one as this comes very close to my incompetence level (not to mention I'm a bit drunk ATM ;)) but...

1. Isn't FLT_MIN a 64-bit value?
2. x86 FPUs internally use 80-bit floats.

So... FLT_MIN / 2.0 would be executed as float80(FLT_MIN) / 2.0 which may explain the discrepencies in the underflow flag handling.

Just a wild guess though, but maybe it can serve as a starting point to the real explanation? :)

---

### Post by hlmuller on 2007-08-10
Alcohol does seem to make this mystery just a little more palatable.  At least after a few pale ales this would seem the case.

According to the Intel architecture (253665.pdf, vol1, p.4-3), the single precision floating numeric data type is 32 bits wide.  the first 23 bits representing the mantissa, the next 8 for the exponent, and the last the sign bit.

One would think that FLT_MIN (float) would correspond with the x86 single precision float width (32-bit).  When the sizeof operator is used on float, it delivers an answer of 4 bytes, which confirms this belief.

But I think you and soybean are hitting close to where the answer lies, and that is in the hardware arena.

Page 8-18, of the above mentioned reference seems to yield a clue which has been mentioned by you and others on the ##c freenode channnel:
> 
"With the exception of the 80-bit double extended-precision floating-point format, all of these data types exist in memory only. When they are loaded into x87 FPU data registers, they are converted into double extended-precision floating-point format and operated on in that format."

Another clue on then next page:

> "As a general rule, values should be stored in memory in  double-precision format. This format provides sufficient range and precision to return correct results with a minimum of programmer attention. The single-precision format is useful for debugging algorithms, because rounding problems will manifest themselves more quickly in this format. The double extended-precision format is normally reserved for holding intermediate results in the x87 FPU registers and constants. Its extra length is designed to shield final results from the effects of rounding and overflow/underflow in intermediate calculations. However, when an application requires the maximum range and precision of the x87 FPU (for data storage, computations, and results), values can be stored in memory in double extended-precision format."

But I'll probably need one more pale ale, a full nights sleep, and additional experimentation to fully understand these implications. 

Regards,

Harv

---

### Post by Soybean on 2007-08-13
> **hlmuller said:**
> By my understanding of the term underflow, attempting to represent a number smaller than FLT_MIN ( otherwise denormal), should set the underflow exception flag.
I think it's just a little subtlety here... I'm pretty sure that trying to calculate *almost* any number less than FLT_MIN will give an underflow. It's just that there are these representable denormal numbers... they are a few (well, about 16 million, but that can be "few" in an infinite space) numbers less than FLT_MIN that can also be accurately represented, without underflow.

Here's a thought: FLT_MIN is obviously not the smallest possible float value, because it's possible to represent zero as a float, right? It's just that zero is a special case in the floating point standard. So are things like infinity and NaN. In the same way, the denormal numbers are special cases; they're valid, accurate numbers (just like zero), but they're represented a bit differently than the normal numbers. So FLT_MIN is the smallest normal number. If you try to calculate something smaller, there's a good chance you'll end up with an underflow error and a loss of precision... unless your calculation happens to yield one of the various "special cases" that are representable less than that (like FLT_MIN/2, or zero). So, in the same way that (FLT_MIN - FLT_MIN) returns zero and doesn't cause an underflow, FLT_MIN / 2 returns another special case without underflow.

Or, looking at it a bit from a lower level:
An underflow at the hardware level basically means "trying to write a 1 bit outside of the range of the register." Extra zero bits don't count as underflow in binary, in the same way that 1.0 == 1.000 in decimal. Also, consider that dividing by 2, in binary, is the same as shifting everything one position to the right (for example, 8 is binary 1000, 4 is 100, 2 is 10, etc). From the wikipedia link, we can see that FLT_MIN, in binary, is a 1 followed by 23 zeros. Dividing by 2 merely pushes a zero out of the register, so it doesn't cause an underflow.  Similarly, dividing by 4 pushes 2 zeros out, and still doesn't cause an underflow. In fact, you'll find that you can divide by any power of 2 up to 2^23 without causing an underflow... but if you divide by 2^24, that solitary 1 bit gets knocked out. The result is zero, and an underflow error, because this time you've lost some precision (in this specific example, you've lost ALL precision!).

I don't know if either of those ways of looking at it will help at all, but I figure they shouldn't hurt. ;)

By the way, it's probably clear by now from the responses you're getting that most people don't really bother to understand floating point numbers at the level of detail you're going for. ;) I program in C++ for a living, and most of the time I just disregard these details as "float magic." I keep in mind that floats are imprecise, but since they're "good enough" for most purposes, I don't usually worry about it much beyond that. My point being that, while trying to understand in detail is good, you probably don't need to get too worried about it. :)

---

