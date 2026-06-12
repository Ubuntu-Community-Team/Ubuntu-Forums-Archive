---
title: "Division and Modulus operators in Python"
date: 2007-07-11
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-11
>>> 10/4
2
>>> -10/4
-3

Why is it ? I think   -10/4 = -2

And now, the Modulus in Python:

>>> 10%4
2
>>> -10%4
2

The operator -10/4 has remainder is -2, not 2

Next:
>>> 10%-4
-2

The operator 10/-4 has remainer is 2, not 2

Next:
>>> 11%4
3
>>> -11%4
1
>>> 11%-4
-1


In this case, I cant understand.

---

### Post by Ex-Cyber on 2007-07-11
Integer division in Python uses the floor instead of rounding toward zero or truncating, so 10/4 = 2.5 becomes 2, while -10/4 = -2.5 becomes -3. The modulo stuff is a bit more subtle and I don't fully understand it, but the two issues are related. Python isn't doing it wrong, it's just trying to produce the most useful answer.

---

### Post by Modred on 2007-07-11
> **mocqueanh said:**
> >>> 10/4
2
>>> -10/4
-3

Why is it ? I think   -10/4 = -2
You misunderstand the math behind the operation because you are thinking in floating point numbers, not integers.  When you divide integers, the result comes from the floor of the fractional result.  Expressing our fractional result as a decimal number, we get 2.5 for the first and -2.5 for the second.  The floor of 2.5 is 2 and the floor of -2.5 is -3.  Consider what the floor operation does: return the closest whole number less than the provided input.  -2 is not less than -2.5, so -2 cannot be the result.

> And now, the Modulus in Python:

>>> 10%4
2
>>> -10%4
2

The operator -10/4 has remainder is -2, not 2
Again your math is off.  A modulus using a positive always returns positive numbers.  If you divide -10 by 4, you have 2 parts of 4 above an even division (being -12).  If you do -11%4, you will get 1, because you have 1 part of 4 above -12.   This seems backward compared to applying modulus to a positive number, but I assure you it is correct.

> Next:
>>> 10%-4
-2

The operator 10/-4 has remainer is 2, not 2
Similar to explanation 1, only now the direction you are moving from number to number is reversed.  With a normal modulus you count from lowest to highest.  Hence -12%4 = 0, -11%4 = 1, -10%4 = 2, and so on.  With a negative number, the accumulation goes the opposite direction: -8%-4 = 0, -9%-4 = -1, -10%-4 = -2, etc.  This is because instead of counting up from the lower number to the higher, you count down from the higher to the lower (we're counting -2 from -8, as opposed to +2 from -12).


> Next:
>>> 11%4
3
>>> -11%4
1
>>> 11%-4
-1


In this case, I cant understand.

I believe my previous explanations have already covered this one.

In short: Python does what it should according to the underlying math.

---

### Post by pmasiar on 2007-07-11
BTW in coming Python 3.0 (AKA Py3K), division of integers will produce float, and we will have separate integer division (//). Guido considers integer division a mistake (against "less surprise" rule), but cannot remove it because of need to backward compatibility. 

Because of Google sponsoring work on Py3K, it is coming to PC next to you in 2008! :-)

---

### Post by mocqueanh on 2007-07-13
thanh you all, now i understand the division math.
My math experience is bad  :KS:KS

---

### Post by spiepie on 2010-07-28
what about 1 % 2 gives 1
11 % 10 gives 1

dont get it 


sorry!!!!

---

### Post by wmcbrine on 2010-07-28
What don't you get? Those are the correct answers.

[http://en.wikipedia.org/wiki/Modulo_operator](http://en.wikipedia.org/wiki/Modulo_operator)

---

### Post by spiepie on 2010-07-29
thanks for your response, I realise that 
1 % 2 gives 1 is the answer but the remainder is not 1.

it seems that % when the answer is a fraction gives 1


i.e 11 % 10 gives 1


but i don't understand why!

thanks for your time

---

### Post by schauerlich on 2010-07-29
> **spiepie said:**
> thanks for your response, I realise that 
1 % 2 gives 1 is the answer but the remainder is not 1.

it seems that % when the answer is a fraction gives 1


i.e 11 % 10 gives 1


but i don't understand why!

thanks for your time

% means the remainder.

when you do 1 / 2, you get a quotient of 0 and a remainder of 1. similarly, when you do 11 / 10, you get a quotient of 1 and remainder of 1. 8 % 3 is 2, 9 % 5 is 4, 13 % 6 is 1, etc.

---

### Post by wmcbrine on 2010-07-29
> **spiepie said:**
> 1 % 2 gives 1 is the answer but the remainder is not 1.Yes, it is. In *integer* division, where 1 / 2 = 0.

> [i]it seems that % when the answer is a fraction gives 1


i.e 11 % 10 gives 1[/i]No, it's just coincidentally 1 in both those cases. 12 % 10 = 2, 13 % 10 = 3. And 9 % 10 = 9.

> *but i don't understand why!*Perhaps if you read the article I linked...

I prefer not to think of it as a "remainder" at all. It's more like, while a > b, a = a - b. This definition may break down outside the range of non-negative integers, but that's normally the range in which the mod operator is used. It's more of a programming thing than a math thing.

P.S. But as I think of it, the whole concept of "remainders" only makes sense in the context of integer division, anyway. So I'm confused as to why you're confused. :)

---

### Post by Sm0ke42o on 2010-08-18
I seem to understand the modulus operator for the most part but this one still confuses the hell out of me. 

```

>>> 12 % 15
12

```

12 / 15 is .8 last time I checked and I understand that the modulus does not always give the result one might expect but 12 just doesn't make sense to me. 

could someone please explain how python is arriving at this result?

thanks.

---

### Post by Bachstelze on 2010-08-18
Third grade math.

12 = 0 × 15 + 12

Quotient is 0, remainder is 12.

```
>>> 12 / 15
0
>>> 12 % 15
12
```

---

### Post by wmcbrine on 2010-08-18
> **Sm0ke42o said:**
> could someone please explain how python is arriving at this result?Did you read this thread at all before posting?

---

### Post by StephenF on 2010-08-18
> **Sm0ke42o said:**
> I seem to understand the modulus operator for the most part but this one still confuses the hell out of me. 

```

>>> 12 % 15
12

```

12 / 15 is .8 last time I checked and I understand that the modulus does not always give the result one might expect but 12 just doesn't make sense to me. 

could someone please explain how python is arriving at this result?

thanks.
Clearly you don't understand.

a % b = a - (a // b * b)

The // means floor division or round down the fractional part.

---

### Post by worksofcraft on 2010-08-18
Remainder always has the same sign as what you divide by.

This is so that it lies between 0 and what you are dividing by.

It is also so that if you do intger division and then multiply again, you just have to add that remainder back in to get your original number.

It all seems quite logical when you think about.

p.s. Here let me put it into 'Python speak' for you:
```


>>> f = lambda x, y: (x//y * y + x%y)
>>> f(7,2)
7
>>> f(7,-2)
7

```

Parlez vous le Python?

---

