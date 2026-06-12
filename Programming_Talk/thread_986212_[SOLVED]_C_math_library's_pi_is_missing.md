---
title: "[SOLVED] C math library's pi is missing"
date: 2008-11-18
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-18
What is pi in C math library? Tried PI & pi but doesn't work.

How can I use pi from math.h?

---

### Post by hod139 on 2008-11-18
There is no cross platform PI available.  If you are only going to use gcc you can use M_PI.  If you want to be cross-platform safe you could do this:
```

#ifndef M_PI
#define M_PI 3.14159265358979323846
#endif

```

---

### Post by crazyfuturamanoob on 2008-11-18
I found PI from somewhere with 500 decimals:
```
3.1415926535897932384626433832795028841971693993751058209749445923078164062862089986280348253421170679821480865132823066470938446095505822317253594081284811174502841027019385211055596446229489549303819644288109756659334461284756482337867831652712019091456485669234603486104543266482133936072602491412737245870066063155881748815209209628292540917153643678925903600113305305488204665213841469519415116094330572703657595919530921861173819326117931051185480744623799627495673518857527248912279381830119491
```
Problem is, that a double-type variable can't handle that many decimals.

I want all 500 decimals to get maximum precision.
But how can that number be fitted in one variable?

---

### Post by Nemooo on 2008-11-18
You can't get a precision of 500 decimals. A double can only ensure as much decimal precision as DBL_DIG says, which is machine dependant:

```
#include <stdio.h>
#include <float.h>

int main(void)
{
    printf("Float can ensure %d decimal places\n", FLT_DIG);
    printf("Double can ensure %d decimal places\n", DBL_DIG);
    printf("Long double can ensure %d decimal places\n", DBL_DIG);

    return 0;
}
```

[http://www.cplusplus.com/reference/clibrary/cfloat/](http://www.cplusplus.com/reference/clibrary/cfloat/)

---

### Post by crazyfuturamanoob on 2008-11-18
> **Nemooo said:**
> You can't get a precision of 500 decimals. A double can only ensure as much decimal precision as DBL_DIG says, which is machine dependant:

```
#include <stdio.h>
#include <float.h>

int main(void)
{
    printf("Float can ensure %d decimal places\n", FLT_DIG);
    printf("Double can ensure %d decimal places\n", DBL_DIG);
    printf("Long double can ensure %d decimal places\n", DBL_DIG);

    return 0;
}
```

[http://www.cplusplus.com/reference/clibrary/cfloat/](http://www.cplusplus.com/reference/clibrary/cfloat/)

Can I get 500 decimals with malloc?

And I read from a book, that there is another float type, **long double**, which can handle twice as much decimals as **double**.

Also, when making it unsigned, decimal amount will get doubled. We don't need memory for negative numbers, when pi is positive.

---

### Post by mike_g on 2008-11-18
For greater precision you would probably want a bignum library eg: [http://gmplib.org/](http://gmplib.org/)

---

### Post by nvteighen on 2008-11-18
> **crazyfuturamanoob said:**
> Can I get 500 decimals with malloc?

And I read from a book, that there is another float type, **long double**, which can handle twice as much decimals as **double**.

Also, when making it unsigned, decimal amount will get doubled. We don't need memory for negative numbers, when pi is positive.
No. malloc() is not the "infinite memory allocator"... it's just a way to allocate stuff in order to have access to it from any call stack where a pointer to it is available. This doesn't happen in automatic stack allocation, in which all variables die after the call stack returns (except, of course, the return value).

You could design a data structure that stores big numbers (BigInt or BigNum)... but it's harder than you might think.

**long double** will give you twice as double. **long long double** variables also exist. And, if I'm not wrong (please someone confirm this!), in a 64-bit architecture, you can even get **long long long double** variables.

**unsigned** data types are a nice trick to get a limit twice as high without using more memory. But, they introduce the possibility of a very subtle bug: if you store a negative number into an unsigned variable, it will be transformed into the modulo opposite (with respect to the variable type's limit + 1). An example: Say we have an unsigned data type that's able to store values from 0 to 5 (that's modulo 6). If I happen to store -1, what I'll get is 6 - 1 = 5. So, doing: "while(unsigned >= 0){unsigned--;}" will lead you to an infinite loop, for example.

---

### Post by Nemooo on 2008-11-18
My 32bit machine has no more than a **long double** type. No **long long double**, and I can't find any information that confirms a **long long double** type, but the opposite is stated.

---

### Post by slavik on 2008-11-18
Thanks for playing. Please try again.

```

slavik@sgoltser:~$ grep -i pi /usr/include/math.h
# define M_PI		3.14159265358979323846	/* pi */
# define M_PI_2		1.57079632679489661923	/* pi/2 */
# define M_PI_4		0.78539816339744830962	/* pi/4 */
# define M_1_PI		0.31830988618379067154	/* 1/pi */
# define M_2_PI		0.63661977236758134308	/* 2/pi */
# define M_2_SQRTPI	1.12837916709551257390	/* 2/sqrt(pi) */
# define M_PIl		3.1415926535897932384626433832795029L  /* pi */
# define M_PI_2l	1.5707963267948966192313216916397514L  /* pi/2 */
# define M_PI_4l	0.7853981633974483096156608458198757L  /* pi/4 */
# define M_1_PIl	0.3183098861837906715377675267450287L  /* 1/pi */
# define M_2_PIl	0.6366197723675813430755350534900574L  /* 2/pi */
# define M_2_SQRTPIl	1.1283791670955125738961589031215452L  /* 2/sqrt(pi) */

```

---

### Post by nvteighen on 2008-11-18
> **Nemooo said:**
> My 32bit machine has no more than a **long double** type. No **long long double**, and I can't find any information that confirms a **long long double** type, but the opposite is stated.
You're right. I confused myself with **long long int**. In some way, you can't have **long long double** is because **double** already "equals" (please, don't take it literally!) a **long float**...

So, can any 64-bit user try whether he/she can use **long long double** or not?

---

### Post by Tony Flury on 2008-11-18
I know this is an aside, but I am curious as to what sort of calculation that isn't some highly precise scientific calculation would need 500 decimal places ?

To be honest if you are doing specialist scientific calculations, I would be tempted to use a specialist toolkit or application.

for instance - even taking the sun as an example (radius 695500 kilometers = 6.955 x10^8 m - precise to only 4 significant figures) which you have to admit is pretty big - and a proton being roughly 1.2x10^-15 m (precise to 2 decimals places)- then you only need pi to 23 places or so to be able to get a measurement in meters of the circumference of the sun to a precision of the radius of a proton.

This does of course make the massive assumption that every single measurement you have is exactly the same or better precision. If you start mixing precision, then the result can only ever be as precise as the least precise measurement.

---

### Post by nvteighen on 2008-11-18
> **slavik said:**
> Thanks for playing. Please try again.

```

slavik@sgoltser:~$ grep -i pi /usr/include/math.h
# define M_PI		3.14159265358979323846	/* pi */
# define M_PI_2		1.57079632679489661923	/* pi/2 */
# define M_PI_4		0.78539816339744830962	/* pi/4 */
# define M_1_PI		0.31830988618379067154	/* 1/pi */
# define M_2_PI		0.63661977236758134308	/* 2/pi */
# define M_2_SQRTPI	1.12837916709551257390	/* 2/sqrt(pi) */
# define M_PIl		3.1415926535897932384626433832795029L  /* pi */
# define M_PI_2l	1.5707963267948966192313216916397514L  /* pi/2 */
# define M_PI_4l	0.7853981633974483096156608458198757L  /* pi/4 */
# define M_1_PIl	0.3183098861837906715377675267450287L  /* 1/pi */
# define M_2_PIl	0.6366197723675813430755350534900574L  /* 2/pi */
# define M_2_SQRTPIl	1.1283791670955125738961589031215452L  /* 2/sqrt(pi) */

```
Thanks... I was sure there was pi in math.h... otherwise, how the hell would trig functions work?

---

### Post by jespdj on 2008-11-18
> **nvteighen said:**
> So, can any 64-bit user try whether he/she can use **long long double** or not?
Let's see:
```
#include <stdio.h>

int main(int argc, char* argv[])
{
	printf("%d\n", sizeof(long long double));
	return 0;
}

```
Nope, doesn't work:
```
jesper@jesper-laptop:~/tmp$ gcc thing.c -o thing
thing.c: In function ‘main’:
thing.c:5: error: both ‘long long’ and ‘double’ in declaration specifiers
```
Doesn't surprise me. The floating-point registers aren't suddenly twice as wide on 64-bit.

---

### Post by hod139 on 2008-11-18
> **slavik said:**
> Thanks for playing. Please try again.

```

slavik@sgoltser:~$ grep -i pi /usr/include/math.h
# define M_PI        3.14159265358979323846    /* pi */

```
<snip>


If you are going to be sarcastic, you should at least make sure your post is 100% correct.
See my post, M_PI is a GNU GCC only constant.  If he needs portability he can't count on that being defined.

---

### Post by slavik on 2008-11-18
MinGW is GNU :)

---

### Post by Honeyisland on 2008-12-01
im trying to compile a C program that uses pow() but there's no pow prototype in my math.h

any ideas?

---

### Post by crazyfuturamanoob on 2008-12-02
> **hod139 said:**
> If he needs portability he can't count on that being defined.

I don't need portability. I make programs for Linux, not windows.

---

### Post by wmcbrine on 2008-12-02
> **Tony Flury said:**
> I know this is an aside, but I am curious as to what sort of calculation that isn't some highly precise scientific calculation would need 500 decimal places ?There aren't any calculations of any kind that require it. The only reason to bother with 500 decimal places of PI is if you just like playing with PI.

---

### Post by geirha on 2008-12-02
> **Honeyisland said:**
> im trying to compile a C program that uses pow() but there's no pow prototype in my math.h

any ideas?

Not in math.h directly, but math.h includes several other headers, and eventually adds a pow prototype with some preprocessor magic. 

```
cpp /usr/include/math.h | grep -w pow
```

Make sure to link with the math library by adding the option '-lm' to the linker command.

BTW, this question would probably have been better off in a separate/new thread.

---

### Post by wmcbrine on 2008-12-02
> **wmcbrine said:**
> There aren't any calculations of any kind that require it. The only reason to bother with 500 decimal places of PI is if you just like playing with PI.P.S. Let me try to put this in perspective... If you were drawing a circle the size of the Earth, and you wanted to ensure that it was perfect down to the atomic level, then twenty-five digits of Pi would be more than enough.

---

### Post by rbprogrammer on 2008-12-02
500 decimal places??? Dear god that is a lot for a calculation.  Nonetheless, has the original poster tried to integrate ruby into his project??

The ruby language has the ability to convert large numbers into strings, then apply mathematical operations upon that string.  Since the primitive datatypes (as stated before) are limited to a certain number of bits, a string can become much larger.

---

### Post by zehdeh on 2013-02-05
here is another site where you can read some informations about float.h http://code-reference.com/c/float.h

---

### Post by wildmanne39 on 2013-02-05
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

