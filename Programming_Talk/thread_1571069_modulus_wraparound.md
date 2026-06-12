---
title: "modulus wraparound"
date: 2010-09-09
forum: Programming Talk
---

### Post by leg on 2010-09-09
Hi,

   I have a piece of code (I'm using Java) that allows an index to to wrap around a range of numbers

```
++num % range
```
which, if range is 4, will give me the output>  0, 1, 2, 3, 0 ...but I would to be able to go in reverse as well does anyone know how to achieve the output > 3, 2, 1, 0, 3 ...

---

### Post by Bachstelze on 2010-09-09
I don't know about Java, but in Python, (-1) % 4 gives 3, so you should be able to just replace ++ with --.

---

### Post by leg on 2010-09-09
> **Bachstelze said:**
> I don't know about Java, but in Python, (-1) % 4 gives 3, so you should be able to just replace ++ with --.Well that's what I thought but doing that gives me the output> -1, -2, -3, 0, -1 ...I have also tried ```
(--num + range) % range
```which works fine for one iteration but then reverts to minus numbers I think the value of -1 screws it up> 3, 2, 1, 0, -1, -2, ...I checked -1 % 4 and it gives me -1

---

### Post by Bachstelze on 2010-09-09
It seems Java has no modulus operator (the % in Java is actually the remainder operator, which is different for negative numbers). So, just add 4 to the index before calculating the remainder:

(3 - 1 + 4) % 4 = 6 % 4 = 2
(2 - 1 + 4) % 4 = 5 % 4 = 1
(1 - 1 + 4) % 4 = 4 % 4 = 0
(0 - 1 + 4) % 4 = 3 % 4 = 3

The trick is that you're working modulo 4, so adding 4 will not change the result. In general:

a mod b = (a + k*b) mod b

for any integer k.

*EDIT:* So yes, try replacing the -- with explicit -1. ++ and -- are just syntactic sugar, and like all sugar, should be consumed with parcimony. ;)

---

### Post by leg on 2010-09-09
> **Bachstelze said:**
> It seems Java has no modulus operator (the % in Java is actually the remainder operator, which is different for negative numbers). So, just add 4 to the index before calculating the remainder:

(3 - 1 + 4) % 4 = 6 % 4 = 2
(2 - 1 + 4) % 4 = 5 % 4 = 1
(1 - 1 + 4) % 4 = 4 % 4 = 0
(0 - 1 + 4) % 4 = 3 % 4 = 3

The trick is that you're working modulo 4, so adding 4 will not change the result. In general:

a mod b = (a + k*b) mod b

for any integer k.

Yes something different about Java modulus but I think it is related to the signed integer causing a problem or so I have read.```
c_num = (char) (--c_num % range);
System.out.println((int)c_num );
```the above gives me what I am after but it is cheating really and no good if the range is too big. You have correctly identified my answer but I had already tried it with the results I posted before. I made an error and wasn't saving num correctly and now that is fixed it works fine. ```
(num = --num + range) % range
```Thanks

---

### Post by Bachstelze on 2010-09-09
> **leg said:**
> You have correctly identified my answer but I had already tried it with the results I posted before. I made an error and wasn't saving num correctly and now that is fixed it works fine. ```
(num = --num + range) % range
```

It seems quite dirty as well. Try replacing the -- with explicit -1 (see my edit).

---

### Post by leg on 2010-09-09
> **Bachstelze said:**
> It seems quite dirty as well. Try replacing the -- with explicit -1 (see my edit).Well I didn't even know how I did it now but ```
(--num + range) % range
```is working as expected. Thanks again.

---

