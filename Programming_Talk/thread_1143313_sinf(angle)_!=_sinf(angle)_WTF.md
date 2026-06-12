---
title: "sinf(angle) != sinf(angle) WTF???"
date: 2009-04-29
forum: Programming Talk
---

### Post by jfbilodeau on 2009-04-29
Hello world,

The following code works as expected on amd64, but not on an i32. Comparing sinf(angle) == sinf(angle) returns false. Any idea why?

```
#include <math.h>
#include <stdio.h>

int main() {
        float angle = M_PI / 2;

        printf("%f, %f\n", sinf(angle), sinf(angle));
        printf("%i\n", sinf(angle) == sinf(angle));
        printf("%i\n", sinf(angle) != sinf(angle));

        return 0;
}
``` 

I'm totally confused. :confused::confused::confused::confused:

---

### Post by samjh on 2009-04-29
You cannot reliably compare two floating point numbers.  It's a problem that computer science hasn't gotten around to solving yet. :)

What you need to do is compare two floating point numbers within a particular magnitude of precision.

So instead of doing a simple logical operation between the two floats, find the difference between the two, and consider them equal if the difference is smaller than some delta.

Example in pseudo-code:
```
delta = ABSOLUTE(SIN(angle1) - SIN(angle2))
IF delta < 0.0000001 THEN
    angles_equal = TRUE
ELSE
    angles_equal = FALSE
```

An example in C, based on your code:
```
#include <math.h>
#include <stdio.h>
#include <stdbool.h>

int main(void)
{
	float angle = M_PI / 2;
	float sin1, sin2, delta;
	bool compresult;

	sin1 = sinf(angle);
	sin2 = sinf(angle);
	delta = fabs(sin1 - sin2);

	if (delta < 0.001) {
		compresult = true;
	} else {
		compresult = false;
	}

	printf("%f, %f\n", sin1, sin2);
	printf("%i\n", compresult);
	printf("%i\n", !compresult);

	return 0;
}
```

---

### Post by jfbilodeau on 2009-04-29
> **samjh said:**
> You cannot reliably compare two floating point numbers.  It's a problem that computer science hasn't gotten around to solving yet. :)

Thanks! I was afraid that would be the answer. The comparison trick you shared with me will be very useful! :)

---

### Post by jimi_hendrix on 2009-04-29
> **samjh said:**
> You cannot reliably compare two floating point numbers.  It's a problem that computer science hasn't gotten around to solving yet. :)


we should really fix that...and get real randoms too :)

---

### Post by Can+~ on 2009-04-29
[PHP]bool floatEquality(float a, float b, float precision)
{
	return (fabs(a - b) < fabs(precision));
}[/PHP]

Reusable. :KS

---

### Post by dwhitney67 on 2009-04-29
> **Can+~ said:**
> [PHP]bool floatEquality(float a, float b, float precision)
{
	if (fabs(a - b) < fabs(precision))
		return true;
	
	return false;
}[/PHP]

Reusable. :KS
Com' on... write leaner code!  Just return the result of the conditional that you test in the if-statement.

---

### Post by Can+~ on 2009-04-29
> **dwhitney67 said:**
> Com' on... write leaner code!  Just return the result of the conditional that you test in the if-statement.

My bad, long time not using C... or any language.

---

### Post by lisati on 2009-04-29
> **dwhitney67 said:**
> Com' on... write leaner code!  Just return the result of the conditional that you test in the if-statement.

D'oh! I think I'm a little rusty with the programming skills, I almost caught myself thinking that it wouldn't work by returning the results of the test. Silly me!

---

### Post by croto on 2009-04-29
I agree with other posts saying that comparing floats by equality is in general a bad idea. However, two floats can of course be equal, and in particular, sinf(x) should be equal to sinf(x).

I believe what's happening here is related to optimization. When optimization is enabled, it happens that even though one define variables as float, for instance, the compiler is free to use the internal registers of the math processor to store results. These are typically larger than double precision. My guess is that in the equality shown by the OP, the numbers are not being compared in the same precision, resulting in FALSE.

I would compile with -O0 to verify that the equality holds as it's defined by the standard. 

That said, except in particular cases, don't compare floats by equality!

---

### Post by jpkotta on 2009-04-30
> **Can+~ said:**
> [PHP]bool floatEquality(float a, float b, float precision)
{
	return (fabs(a - b) < fabs(precision));
}[/PHP]

Reusable. :KS

I've used 
```
b != 0 && abs(a/b - 1) < 10*epsilon
```
in the past.  I can't remember why I did that instead of Can+~'s.

---

### Post by jespdj on 2009-04-30
> **jpkotta said:**
> I've used 
```
b != 0 && abs(a/b - 1) < 10*epsilon
```
in the past.  I can't remember why I did that instead of Can+~'s.
That's tricky, because the division can give you rounding errors and what if a == b == 0? I'd prefer the fabs(a - b) < fabs(precision) version.

---

### Post by jfbilodeau on 2009-04-30
> **croto said:**
> I believe what's happening here is related to optimization. When optimization is enabled, it happens that even though one define variables as float, for instance, the compiler is free to use the internal registers of the math processor to store results. These are typically larger than double precision. My guess is that in the equality shown by the OP, the numbers are not being compared in the same precision, resulting in FALSE.

I would compile with -O0 to verify that the equality holds as it's defined by the standard. 

Just to add a bit to the funk, I tried compiling with -O0 and got the same result. However, compiling with -O1 and above works correctly -- that is sinf(x) == sinf(x).

It's strange that this behaviour seems to happen only when optimizations are disabled. :P

EDIT:
Actually, it's not that strange. I looked at the assembly code generated, and the compiler seems to be smart enough to avoid calling sinf twice, and realizes that the comparison should always == true.

```

main:
        leal    4(%esp), %ecx
        andl    $-16, %esp
        pushl   -4(%ecx)
        pushl   %ebp
        movl    %esp, %ebp
        pushl   %ecx
        subl    $36, %esp
        fld1
        fstl    16(%esp)
        fstpl   8(%esp)
        movl    $.LC1, 4(%esp)
        movl    $1, (%esp)
        call    __printf_chk
        movl    $1, 8(%esp)  // Load true (1)
        movl    $.LC2, 4(%esp)
        movl    $1, (%esp)
        call    __printf_chk
        movl    $0, 8(%esp)  // Load false (0)
        movl    $.LC2, 4(%esp)
        movl    $1, (%esp)
        call    __printf_chk
        movl    $0, %eax
        addl    $36, %esp
        popl    %ecx
        popl    %ebp
        leal    -4(%ecx), %esp
        ret

```

J-F

---

### Post by Npl on 2009-04-30
> **jfbilodeau said:**
> Hello world,

The following code works as expected on amd64, but not on an i32. Comparing sinf(angle) == sinf(angle) returns false. Any idea why?

```
#include <math.h>
#include <stdio.h>

int main() {
        float angle = M_PI / 2;

        printf("%f, %f\n", sinf(angle), sinf(angle));
        printf("%i\n", sinf(angle) == sinf(angle));
        printf("%i\n", sinf(angle) != sinf(angle));

        return 0;
}
``` 

I'm totally confused. :confused::confused::confused::confused:gcc uses SSE2 operations for AMD64 which are deterministic - means they return the same output for the same input each time.

gcc on x86 uses the x87 FPU by default which is one of the most ackward things in existence. You could use SSE2 instead of the FPU by using the options "-msse2 -mfpmath=sse", ofcourse the executeable wont run on CPUs without SSE anymore.

---

### Post by jfbilodeau on 2009-05-06
> **Npl said:**
> gcc uses SSE2 operations for AMD64 which are deterministic - means they return the same output for the same input each time.

gcc on x86 uses the x87 FPU by default which is one of the most ackward things in existence. You could use SSE2 instead of the FPU by using the options "-msse2 -mfpmath=sse", ofcourse the executeable wont run on CPUs without SSE anymore.

Thanks. That's exactly what happened, and clarifies it for me. :)

---

### Post by Krupski on 2009-05-07
> **samjh said:**
> You cannot reliably compare two floating point numbers.  It's a problem that computer science hasn't gotten around to solving yet. :)

I understand that floating point math is not perfectly accurate on a computer... but why should two calls with the SAME input return a different OUTPUT each time?

I know, for example, that ((10 / 3) * 3) may not equal exactly 10.000000, but (10 / 3) should EQUAL (10 / 3) because it's the same call!

Or am I missing something?

---

### Post by Npl on 2009-05-07
> **Krupski said:**
> I understand that floating point math is not perfectly accurate on a computer... but why should two calls with the SAME input return a different OUTPUT each time?That would be a perfectly sane assumption, unfortunatly the x87 FPU is something where you dont get far with sanity.

Its impossible to say for sure what exactly happens without looking at the assembly, but well... internal registers are 80 bit, and compilers often need to store results on the stack, when they will get truncated to 64 or 32 bit. And it has to do ALOT of these stack-operations as you cant specify directly which registers you want to work on.

So what couldve happened is something like this:
calculate result1 = sin( angle )
store result1 on stack (truncating to 32bit)
calculate result2 = sin( angle )
compare result2(80 bit accuracy) with result1 (32bit accuracy)
complain results are not the same

---

### Post by jfbilodeau on 2009-05-07
> **Npl said:**
> That would be a perfectly sane assumption, unfortunatly the x87 FPU is something where you dont get far with sanity.

Its impossible to say for sure what exactly happens without looking at the assembly, but well... internal registers are 80 bit, and compilers often need to store results on the stack, when they will get truncated to 64 or 32 bit. And it has to do ALOT of these stack-operations as you cant specify directly which registers you want to work on.

So what couldve happened is something like this:
calculate result1 = sin( angle )
store result1 on stack (truncating to 32bit)
calculate result2 = sin( angle )
compare result2(80 bit accuracy) with result1 (32bit accuracy)
complain results are not the same

I'm curious. How come the conversion from 80bit to 32bit would result in different bit patterns? I have to admit I don't know much about the x87.

---

### Post by Npl on 2009-05-07
> **jfbilodeau said:**
> I'm curious. How come the conversion from 80bit to 32bit would result in different bit patterns? I have to admit I don't know much about the x87.
Well, you lose accuracy?
Consider pi with 9 decimals accuracy
3,14159265
round it towards 4 decimals:
3,142

Now compare them.

---

### Post by jfbilodeau on 2009-05-08
> **Npl said:**
> Well, you lose accuracy?
Consider pi with 9 decimals accuracy
3,14159265
round it towards 4 decimals:
3,142

Now compare them.

Agreed, but if I round pi to four decimals twice, and compare both values, should I not have the same result? :confused:

---

### Post by Npl on 2009-05-09
> **jfbilodeau said:**
> Agreed, but if I round pi to four decimals twice, and compare both values, should I not have the same result? :confused:Nope, you compare the rounded value (loaded from stack) with the unrounded one (directly from the calculation). Read up on x87 and look at disassemblies... its a mess I dont want to explain( and couldnt either unless I read alot documentation ).

---

