---
title: "[C++] Understanding the Difference Between &amp; and &amp;&amp;"
date: 2011-03-01
forum: Programming Talk
---

### Post by dodle on 2011-03-01
I am having trouble understanding the difference between the logical [color=blue]&&[/color] and the bitwise [color=blue]&[/color]. I understand how the logical works, but I don't understand how the bitwise works. I will try to demonstrate my confusion in the code below.

example:
[php]// Evaluating using logical operator &&
(4 && 5); // 4 is non-zero and 5 is non-zero, evaluates to true (1)

// Evaluating using bitwise operator &
(4 & 5); // Evaluates to 4
(2 & 5); // Evaluates to 0[/php]

I am not sure why either of that last two evaluate the way they do. I have a book on C++, but it does not give any information on the bitwise operator. I have also looked over operators at [cplusplus.com](http://www.cplusplus.com/doc/tutorial/operators/), but it doesn't say much about the bitwise operator.

---

### Post by johnl on 2011-03-01
'bitwise' means it operates on a bit-level.  Are you familiar with binary representation of a number?

consider the number 243.  In base 10, this is 243.  think about how that works. each digit from right to left is multiplied by increasing power of 10, e.g. 

```

3*10^0 = 3*1   = 3
4*10^1 = 4*10  = 4
2*10^2 = 2*100 = 200

```

For other bases, you multiply instead by other powers; for example, hexadecimal (base-16) uses A-F to represent the numbers 10-15, and each digit represents a multiple of a powers of 16.

Binary is base 2, so each digit represents a power of 2.

```

base-10:   243    [1*3 + 10*4 + 100*2]
base-16:    F3    [1*3 + 16*15]
base-2:  11110011 [1*1 + 2*1 + 4*0 + 8*0 + 16*1 + 32*1 + 64*1 + 128*1]

```

E.g. 243:

```

256 128 64 32 16 8 4 2 1
  0   1  1  1  1 0 0 1 1

```

bitwise operators operate on a per-bit level.  So let's look at one of your examples:

```

4 = 00000100  // 'four' bit set
5 = 00000101  // 'four' bit and 'one' bit set

00000100 (4) & // AND: only keep bits set in both
00000101 (5)
--------
00000100 (4)


00000100 (4) | // OR: keep bits set in either
00000101 (5)
--------
00000101 (5)

00000100 (4) ^ //  EXCLUSIVE OR: keep bits only set in one but not the other
00000101 (5)
--------
00000001 (1)

```

Does this help?  I'm sure if you google you can find an intro to binary numbers and bitwise operators.

---

### Post by dodle on 2011-03-01
Yes, that clears things up very nicely. Thank you much. :)

---

### Post by SledgeHammer_999 on 2011-03-02
Another great article(IMO) is this:
[http://www.cprogramming.com/tutorial/bitwise_operators.html](http://www.cprogramming.com/tutorial/bitwise_operators.html)

---

### Post by dodle on 2011-03-02
> **SledgeHammer_999 said:**
> Another great article(IMO) is this:
[http://www.cprogramming.com/tutorial/bitwise_operators.html](http://www.cprogramming.com/tutorial/bitwise_operators.html)

Yes, that is a very good article, thank you.

---

### Post by rnerwein on 2011-03-03
hi
just an example what you can do with that bitwise operations ( how to swap two integers without another field).
try this code - :-)
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>


int main(void)
{
int i = 9;
int x = 1;
fprintf(stderr,"i = %d - x = %d\n",i,x);
i ^= x;
x ^= i;
i ^= x;
fprintf(stderr,"after the exclusive operations: i = %d - x = %d\n",i,x);
exit(0);
}
ciao

---

