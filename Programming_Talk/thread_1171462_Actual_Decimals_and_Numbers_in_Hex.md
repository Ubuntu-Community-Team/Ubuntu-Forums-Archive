---
title: "Actual Decimals and Numbers in Hex"
date: 2009-05-27
forum: Programming Talk
---

### Post by Jmoo on 2009-05-27
I'm currently sending a protocol over udp using c.  My question is if I have a float that equals say 0.5324 and I have 4 bytes of hex that I must send that number over udp in.  What would the hex numbers be?  What is the 4 byte representation in hex of a float that equals 0.5324 or 0.23 or -0.43 or 1.45 for that matter.

Thanks in Advance

---

### Post by Zugzwang on 2009-05-27
There are different encodings for floating point numbers. Normally, it should be mentioned in the specification of the protocol you are working on which one is taken. The IEEE 754 standard is the most commonly used one:

[http://en.wikipedia.org/wiki/IEEE_754-1985](http://en.wikipedia.org/wiki/IEEE_754-1985)

Note that floating point numbers are subject to limited precision. So there's no number that *equals* 0.5324, just one that's a close number to it. If your program is meant to run on an x86 processor (and IEEE 754 encoding is to be used), it is likely that you can simply cast your float number to an integer one in order to get the number. I only know the following possibility, there should be better ones:

```

float value = 0.523;
int *where = (int*)(&value);
int encoded = *where;

```

---

### Post by Habbit on 2009-05-27
A probably-unneeded clarification: the code provided by Zugzwang is correct, but the explanation is not. You should not cast _the number_ to int (that would truncate it), but take its address and then use it as a pointer-to-int, which is what the code does. In C++ terminology, a "reinterpret_cast<int*>(&value)".

---

### Post by Jmoo on 2009-05-27
Great Answers.  You've pointed me in the right direction.  Thanks.

---

