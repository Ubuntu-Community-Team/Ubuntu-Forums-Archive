---
title: "Really Big number"
date: 2012-05-04
forum: Programming Talk
---

### Post by shashanksingh on 2012-05-04
I want to find the number of trailing zeroes in a really big number, which is a factorial of a long number.

I have attatched a CPP file herewith. I think the problem here is that

```
fmod(fact,denominator)
```

gives me the correct answer for factorial of 22 and denominator as 10.00 (which is 0.000).

But it gives me the wrong answer for factorial of 23 and denominator as 10.00
:confused:

---

### Post by Arndt on 2012-05-04
> **shashanksingh said:**
> I want to find the number of trailing zeroes in a really big number, which is a factorial of a long number.

I have attatched a CPP file herewith. I think the problem here is that

```
fmod(fact,denominator)
```

gives me the correct answer for factorial of 22 and denominator as 10.00 (which is 0.000).

But it gives me the wrong answer for factorial of 23 and denominator as 10.00
:confused:

Ah, a classical homework task. There are shortcuts. But have you printed out and looked at the numbers before doing the modulo operation?

---

### Post by ofnuts on 2012-05-04
> **shashanksingh said:**
> I want to find the number of trailing zeroes in a really big number, which is a factorial of a long number.

I have attatched a CPP file herewith. I think the problem here is that

```
fmod(fact,denominator)
```gives me the correct answer for factorial of 22 and denominator as 10.00 (which is 0.000).

But it gives me the wrong answer for factorial of 23 and denominator as 10.00
:confused:You can't use floating point computation for this... you very quickly produce numbers with more digits than will fit in the mantissa. You would get a bit more room in 64-bit integers.

But of course you don't need to compute the factorial at all.

---

### Post by Odexios on 2012-05-05
Before starting to make any kind of calculation, think about the problem; a number has a number of trailing zeroes equal to the number of times it is divisible by 10, which is 2*5.

A simple way to avoid the factorial is to work around this idea, and keeping in mind what a factorial is.

---

### Post by shashanksingh on 2012-05-06
> **Odexios said:**
> Before starting to make any kind of calculation, think about the problem; a number has a number of trailing zeroes equal to the number of times it is divisible by 10, which is 2*5.

A simple way to avoid the factorial is to work around this idea, and keeping in mind what a factorial is.

Thank you. I realized the solution is to just find the number of 5's in a factorial. :) and that worked. I also realized I could define 64bit int by int64_t

---

