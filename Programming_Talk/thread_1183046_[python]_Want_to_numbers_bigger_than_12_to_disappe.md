---
title: "[python] Want to numbers bigger than 12 to disappear"
date: 2009-06-09
forum: Programming Talk
---

### Post by swoll1980 on 2009-06-09
I want to write a simple time program. I want sums bigger than 12 to be 0 + (the difference between the sum, and twelve) How would I do that. For example 9+9 would be 6 not 18. It has to work both ways so 
6-9 would also be 9 The easiest way I can think would  be to have it reset to 0 at 12, but I don't know how to do it.

---

### Post by shadylookin on 2009-06-09
use mod 

(9 + 9) % 12 = 6

---

### Post by SSTwinrova on 2009-06-09
Mod is the correct operator to use here. However, to just give you some more perspective, you could also do something along the lines of the following:

*Perform addition/subtraction
*Have a loop that runs while your sum is > 11 or < 0:
**If > 11, subtract 12 from the sum
**If < 0, add 12 to the sum

At an extremely basic level, you could argue that this is what mod is really doing "behind the scenes".

---

### Post by Can+~ on 2009-06-09
> **SSTwinrova said:**
> At an extremely basic level, you could argue that this is what mod is really doing "behind the scenes".

Mod is just the remainder of integer division.

```

1200 / 32 = 37
_-96_
 240
_-224_
  16
```

---

### Post by swoll1980 on 2009-06-09
I'm not sure what you guys are talking about, but you gave me a push in the right direction. I will study the mod operator, and see exactly what it does, and how I can use it. Thanks a bunch.

---

### Post by swoll1980 on 2009-06-09
> **SSTwinrova said:**
>  you could also do something along the lines of the following:

*Perform addition/subtraction
*Have a loop that runs while your sum is > 11 or < 0:
**If > 11, subtract 12 from the sum
**If < 0, add 12 to the sum


This is what I was thinking of doing. I thought there might be a better way of doing it. I will learn how mod works, and go from there.

---

### Post by konungursvia on 2009-06-09
Of course it's mod, which is short for modulus, a clock like circular counting mechanism. The clock is mod-12, which resets to 1 after 12 instead of 13. That's exactly what you asked for.

---

### Post by Can+~ on 2009-06-09
> **swoll1980 said:**
> This is what I was thinking of doing. I thought there might be a better way of doing it. I will learn how mod works, and go from there.

Mod has nothing special to it, is just another arithmetic operator.

The easiest way to see it is with Fractions:

```
_ 1_
10
```

If you were to calculate the integer quotient and modulus, you would obtain:

1/10 = 0
1%10 = 1

Now let's make the number grow, let's say 27/10, but it can also be expressed on mixed notation

```
_27_ = 2+_ 7_
10     10
```

The number fits two (2) and seven tenths (7/10) in ten:

27/10 = 2
27%10 = 7

In other words, with your integer division you always get the "entire" part and with modulus you get the numerator.

This means that for a set of rational numbers, let's say:

```

_ 1_ _ 2_ _ 3_ _ 4_ _ 5_ _ 6_ _ 7_ _ 8_ _ 9_ _10_ _11_
10 10 10 10 10 10 10 10 10 10 10
```

```

_ 1_ _ 2_ _ 3_ _ 4_ _ 5_ _ 6_ _ 7_ _ 8_ _ 9_  1 1+_ 1_
10 10 10 10 10 10 10 10 10      10
```

The modulus will "loop" over 0 and 9, or, in a more general form, if the divisor is N, modulus will go from 0 to N-1.

---

### Post by benj1 on 2009-06-10
either do
```

while time > 12:
    time = time-12
```

or modulo

```
time = time % 12
```
modulo is just what is left over after dividing whole number integers
eg 15/12 would give you 1, the remaining 3 isn't divided
15%12 would give you 3, the remainder after dividing the 15 by 12
so 15.00 (3pm) would be 15%12 would give you 3 (pm)

---

### Post by fiddler616 on 2009-06-10
+1 for modulo. This example aside, it's a very important skill to know for programming.

---

### Post by Ariel David Moya Sequeira on 2009-06-11
I'd go with the Modulo operation. In fact, it's the basis of all mathematical and computational data representations. Almost everything that resets when it reaches some limit (like the counter you want to implement) uses the modulo operation.

---

