---
title: "CPUs can't multiply"
date: 2007-11-05
forum: Programming Talk
---

### Post by slavik on 2007-11-05
Today, I will explain how CPUs actually multiply (somewhat).

A circuit for a "full adder" is very simple to build (I might do a post on it later). The problem comes with multiplying two numbers ... which the CPU can't do. CPUs multiply by actually using repeated addition (the way we are taught in whatever single digit grade (depending on your locale)), so 5*7 becomes 5+5+5+5+5+5+5.

Here is simple code in C (I chose C for a specific reason to be seen further below):
[php]
/* We are going to assume that multiplying x and y will not overflow 4 bytes (32bits) and we are doing multiplication on positive unsigned numbers. */
int mul(int x, int y) {
  int result = 0;
  while (y--) result +=x;
  return result;
}
[/php]

The above method is nice and peachy, except it has a complexity of O(y) (meaning you need to do about y amount of operations). But, it is actually possible to do better. To do better we need to move over to binary space. :)

(Using 4 bits for numbers)
5 in binary is 0101
7 in binary is 0111

The idea is simple. Start the result at 0 like in the previous example. Using long multiplication method from the same single digit grade we multiply the two numbers, we get the following:
```

   0101
   0111
   ------
   0101
  0101
 0101
0000
---------
0100011

```

notice how the fourth row is all zeros when we multiply. Also notice how the fives are positioned.

The ides is to take the least significant bit in the multiplier (y) and if it is 1 then add x to result. Then we shift x left 1 bit (thereby multiplying it by 2) and take the second least significant digit from (y) and repeat the process until we run out of bits in y. The problem is, how do we go through bits in y? Simple really, we shift y to the right (giving us the effect of dividing by 2) and then we use the binary logical AND on y and 0x01. If the result is 1 (true) then we know that the least significant bit is 1, if it's 0, then the bit is 0.

Here is what it looks like in C:
[php]
int mul(int x, int y) {
  int result = 0;
  while (y != 0) {
    if (y & 0x01) result += x;
    y >>= 1;
    x <<= 1;
  }
  return result;
}
[/php]

But the question is why would this be faster than the previous version? for once, the bit shifts take only 1 clock cycle to happen. The AND operation also takes one cycle. The comparison however takes as many cycles as an add instruction plus the changing of the IP (Instruction Pointer). What we are winning on is having to do much less loops when adding large numbers that may have many zeros in their binary representation.

PS: Another thing is that the integer division instructions in x86 assembly, give you both the quotient and the remainder. So something like 5/6 and 5%6 can be done in a single division instruction. :)

---

### Post by santiagoward2000 on 2007-11-05
I'll teach my CPU to multiply! :lolflag:

---

