---
title: "C - What's longer than an 'unsigned long long'?"
date: 2010-10-18
forum: Programming Talk
---

### Post by BioBiro on 2010-10-18
Hi all! I'm trying to write a bit of C code that generates the sum of n^n, with n increasing by 1 each time up to 1000. I apologise in advance for my total newbieness:

```
#include <stdio.h>
#include <math.h>

unsigned long long square(int, int);

main()
{
    int i;
    int powerof;
    unsigned long long temp;
    int base;
    unsigned long long result;
    
    powerof = temp = base = result = 0;
    
    for (i = 1; i < 1001; ++i) {
        base = base + 1;
        powerof = powerof + 1;
/*        temp = square(base, powerof);*/
        temp = pow(base, powerof);
        result = result + temp;
        printf("%d,%d,%llu,%llu\n", base, powerof, temp, result);
    }
}
```It only manages to get up to 15^15 :confused::

```
1,1,1,1
2,2,4,5
3,3,27,32
4,4,256,288
5,5,3125,3413
6,6,46656,50069
7,7,823543,873612
8,8,16777216,17650828
9,9,387420489,405071317
10,10,10000000000,10405071317
11,11,285311670611,295716741928
12,12,8916100448256,9211817190184
13,13,302875106592253,312086923782437
14,14,11112006825558016,11424093749340453
15,15,437893890380859392,449317984130199845
16,16,0,449317984130199845

```So I wrote my own power function like this...

```
unsigned long long square(int base, int powerof)
{
    int i;
    unsigned long long squarefunc;
    
    squarefunc = 1;

    for (i = powerof; i > 0; --i)
        squarefunc = squarefunc * base;
    return squarefunc;
} 

```...and it also screwed up past 15. To make sure nothing was really dodgy (other than me), I checked the calculation manually like this...

```
#include <stdio.h>
#include <math.h>

main()
{
    printf("%f", pow(16, 16));
}
```...and it gave me the correct answer of 18446744073709551616. However, this number is the maximum value a 64-bit unsigned variable can hold (e.g. 0xFFFFFFFFFFFFFFFF).

Any ideas chaps? :P[SIZE=1]
[/SIZE]

---

### Post by worksofcraft on 2010-10-18
yes... use a different language.

Python automatically switches to "infinite" precision bignum numbers for you so that you can calculate really useful things like 1000^1000 with exact precision.

Incidentally I don't want to ruin the suspense but it is a 1 followed by 3000 zero's :shock:

---

### Post by BioBiro on 2010-10-18
> **worksofcraft said:**
> really useful things like 1000^1000 with exact precision.

Lol.

Thanks []("http://ubuntuforums.org/member.php?u=386585")worksofcraft - i'll do it in Python instead. You solved my other ASM question too, so double thanks :P. In the last couple of months i've learnt the basics of four different languages (Bash > Python > Assembler > C). Once I start learning one, I notice some buzz about another and start learning that one instead. They're all such fun I can't make my mind up...

---

### Post by worksofcraft on 2010-10-19
> **BioBiro said:**
> Lol.

Thanks []("http://ubuntuforums.org/member.php?u=386585")worksofcraft - i'll do it in Python instead. You solved my other ASM question too, so double thanks :P. In the last couple of months i've learnt the basics of four different languages (Bash > Python > Assembler > C). Once I start learning one, I notice some buzz about another and start learning that one instead. They're all such fun I can't make my mind up...

Yes I see your point. There are so many computer languages it's hard to know what to choose. However many of them just seem to offer more of the same with different syntax.

What would probably serve you better is to look at some radically **different** ideas in programming.

I'm far from competent to give good advice on this, but for a start I think you will really benefit from exploring the concepts of object oriented programming. I suspect that if you find out what is "polymorphism" and create a program that actually uses it, you will really enjoy your learning ;)

---

### Post by schauerlich on 2010-10-19
> **worksofcraft said:**
> yes... use a different language.

Python automatically switches to "infinite" precision bignum numbers for you so that you can calculate really useful things like 1000^1000 with exact precision.

Incidentally I don't want to ruin the suspense but it is a 1 followed by 3000 zero's :shock:

Seems we've come around. :)

---

### Post by worksofcraft on 2010-10-19
> **schauerlich said:**
> Seems we've come around. :)

Yes :)

Indeed, calculating 1000^1000 is even **more** appropriate application for bignums than that of recording the distance from Christchurch to the moon and back in nanometers which I mentioned in that other thread was pushing 64 bit longs near their limit ;)

---

### Post by nlneilson on 2010-10-19
Python is an excellent language to start with.

Java is very good also, an interpreted language the same as Python and has $$$ support with Oracle.

C/C++ is a native compiled (machine code) language, harder to learn and slower to code in but the power and speed is hard to beat.

as worksofcraft mentioned some languages are different for max
max int = 2^31 - 1 = 2147483647
max unsigned int = 2^32 - 1 = 4294967295
max float = 2^(2^7) = 3.4 x 10^38
max double = 2^(2^10) = 1.798 x 10^308
max long double is about 2^(2^14) = 1.19 x 10^4932.

Your program may have finished before the printing is finished.

You are correct on this:
"However, this number is the maximum value a 64-bit unsigned variable can hold (e.g. 0xFFFFFFFFFFFFFFFF)."

---

### Post by BioBiro on 2010-10-19
Thanks for the advice worksofcraft - I will look into OO with Python for a good start. :)

As usual Python makes short work of things with the help of it's long/bignum integer type:

```
i = 0
base = 0
power = 0
temp = 0
sum = 0

for i in range(1000):
    i = i + 1
    base = base + 1
    power = power + 1
    temp = base ** power
    sum = sum + temp
    print(base,power,temp,sum)
```

For those curious - this is [problem 48 on Project Euler]("http://projecteuler.net/index.php?section=problems&id=48")!

---

### Post by MarkieB on 2010-10-21
no longer participating in ubuntuforums.org

---

### Post by sujoy on 2010-10-21
or if you need a C solution, look into [this]("http://gmplib.org")

---

### Post by NovaAesa on 2010-10-21
This particular project euler problem really isn't that hard to solve without resorting to using bignums. Consider that the problem only requires the last 10 digits of the sum in question... if you take the modulo 10^10 at almost every step (you don't have to do all of them) you won't have any overflow problems.

---

### Post by worksofcraft on 2010-10-21
> **NovaAesa said:**
> This particular project euler problem really isn't that hard to solve without resorting to using bignums. Consider that the problem only requires the last 10 digits of the sum in question... if you take the modulo 10^10 at almost every step (you don't have to do all of them) you won't have any overflow problems.

+1
Yes :)

I somehow suspect this "project Euler" was not really intending us to write noddy 3 line programs that use brute force processing power ;)

---

### Post by BioBiro on 2010-10-23
> **NovaAesa said:**
> This particular project euler problem really isn't that hard to solve without resorting to using bignums. Consider that the problem only requires the last 10 digits of the sum in question... if you take the modulo 10^10 at almost every step (you don't have to do all of them) you won't have any overflow problems.

Thanks NovaAesa! I didn't understand what you said at first, but when I was going to sleep I thought about it again and it made sense. E.g.:

48635406545904734 mod 10^10 (or might just use the constant 10000000000) = 6545904734

93759375037555931 mod 10^10 = 5037555931

48635406545904734 + 93759375037555931 = 14239478**1583460665**

6545904734 + 5037555931 = 1**1583460665**

I dunno how you come up with this stuff but i'm stealing this one for myself :P.

---

### Post by CptPicard on 2010-10-23
> **worksofcraft said:**
> 
I somehow suspect this "project Euler" was not really intending us to write noddy 3 line programs that use brute force processing power ;)

It is actually quite typical of Project Euler problems that pretty much all of them have some discrete math properties at their root that allow for efficient solutions. In that sense they're pretty boring as *programming* exercises... once you get the "trick" to the problem, rest is just fairly boring implementation.

I've got to give it to them though that they do force uninsightful brute-force implementers to do a lot of work in vain :)

---

