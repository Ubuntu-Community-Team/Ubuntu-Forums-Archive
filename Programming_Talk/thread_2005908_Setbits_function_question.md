---
title: "Setbits function question"
date: 2012-06-18
forum: Programming Talk
---

### Post by stamatiou on 2012-06-18
I have found this exercise in k&r: [http://clc-wiki.net/wiki/K%26R2_solutions:Chapter_2:Exercise_6](http://clc-wiki.net/wiki/K%26R2_solutions:Chapter_2:Exercise_6) but I can't understand what each expression should do. Can someone help me a bit?

---

### Post by 11jmb on 2012-06-18
~  is the bitwise complement: ~00110101 = 11001010
<< is a left bitwise shift: 00001110<<2 = 00111000
& is a bitwise AND: 11111010 & 11001100 = 11001000
| is a bitwise OR: 11111010 | 11001100 = 11111110

Hope that helps :)

---

### Post by dwhitney67 on 2012-06-18
I do not have too much time on hand to discuss all of the details of the application, but just to help a bit:

~ is used to make the one's complement of a number.

<< performs a left-shift of N bits in a value (a shift of 1 bit is similar to multiplying by 2)

>> performs a right-shift of N bits in a value (a shift of 1 bit is similar to dividing by 2)

So, at ~0 is equivalent to the largest unsigned value (int?), which in hex would be 0xFFFFFFFF.  If you shift this value by one bit to the left, the result would be 0xFFFFFFFE.

Note, translation of hex to binary:

0xF = 1111
0xE = 1110
0xD = 1101
...
0x2 = 0010
0x1 = 0001
0x0 = 0000

---

### Post by stamatiou on 2012-06-18
Thank you for the quick replies.

Excuse me for not being accurate, but I mean how exactly the function works. For example the part:
```
msk << p + 1 - n
``` moves the mask to the point were desire bits begin, but I can not understand what the other expressions' purposes are.

---

### Post by dwhitney67 on 2012-06-18
Take 'p' plus one minus 'n'; then left-shift 'msk' by that number.

Btw, the statement could be interpreted differently by various compilers.  It could be to shift 'msk' by 'p', and then perform the other arithmetic.  I would suggest that you place parenthesis around the operations that you want to have precedence.  IMO, the point of the statement is to perform what I stated in my opening sentence.

---

### Post by trent.josephsen on 2012-06-18
> **dwhitney67 said:**
> Take 'p' plus one minus 'n'; then left-shift 'msk' by that number.

Btw, the statement could be interpreted differently by various compilers.  It could be to shift 'msk' by 'p', and then perform the other arithmetic.  I would suggest that you place parenthesis around the operations that you want to have precedence.  IMO, the point of the statement is to perform what I stated in my opening sentence.
Left and right shift have lower precedence than + and -, so that expression is guaranteed to behave as `msk << (p + 1 - n)` for any compiler that compiles C.

However, I'd leave the parentheses in anyway, so that people like me don't have to look up operator precedence tables to determine what the expression does. For anything more complicated than +-*/, this is probably a good idea.

---

