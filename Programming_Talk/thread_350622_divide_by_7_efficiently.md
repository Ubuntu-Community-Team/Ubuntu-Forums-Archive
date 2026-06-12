---
title: "divide by 7 efficiently"
date: 2007-01-31
forum: Programming Talk
---

### Post by krypto_wizard on 2007-01-31
How to divide a number by 7 efficiently without using - or / operator. We can use the bit operators. I was thinking about bit shift operator but I don't know the correct answer.

---

### Post by lloyd mcclendon on 2007-01-31
wait i forgot we can't use /

LOL

---

### Post by Wybiral on 2007-02-01
Well, bit shifts work great for fast power of two division/multiplication, such as...

```

x>>1  = x/2
x>>2  = x/4
x>>3  = x/8
x>>4  = x/16
x>>5  = x/32
x>>6  = x/64
x>>7  = x/128
x>>8  = x/256
x>>9  = x/512
x>>10 = x/1024

x<<1  = x*2
x<<2  = x*4
x<<3  = x*8
x<<4  = x*16
x<<5  = x*32
x<<6  = x*64
x<<7  = x*128
x<<8  = x*256
x<<9  = x*512
x<<10 = x*1024

```

But only power of two numbers, I don't know of any way that you can use them for non-power of twos (because of how they work).

0001 = 1
(0001 << 1) = 0010 = 2
(0010 << 1) = 0100 = 4
(0100 >> 2) = 0001 = 1

Bit shifts only work for integer numbers too.

---

### Post by amo-ej1 on 2007-02-01
But you can use approximations that way.

```

1/7 = 0.142857

Now 1/8 + 1/64 = 0.140625
Or
1/8+1/64+1/512 = 0.142578

```

---

### Post by krypto_wizard on 2007-02-01
I think your solution is the closest I can get.

Thanks

---

### Post by Klipt on 2007-02-01
If you want to divide n by 7 you could do a binary search for the x that satisfies x*7 = n. Binary search requires being able to divide by 2, but that's easy with bitshifting (x/2 = x>>1)

---

### Post by Lux Perpetua on 2007-02-01
There are also recursive algorithms based on binary representation. For example, think of how you might get x/7 and x%7 if you had (x/2)/7 and (x/2)%7 from a recursive call. The way I'm thinking of traditionally requires some subtraction, but since your divisor is always 7, you can get around it. 

It might help to think of it this way: (a/b)*b + (a%b) == a.

---

### Post by Ragazzo on 2007-02-01
Or to be simple, multiply by 0.142857

---

### Post by lloyd mcclendon on 2007-02-01
^ yeah but what's the point of that.  at some point you used a / somewhere.

how about efficient division by N without using / or -

---

### Post by Npl on 2007-02-01
int32_t result = (int32_t)(((int64_t)x * 613566757U) >> 32)

This is (at least) exact for values smaller than 2^24. afterwards you can have a result thats 1 lower as the exact calculation (its still exact for most values).

---

### Post by gummibaerchen on 2007-02-02
> **krypto_wizard said:**
> I think your solution is the closest I can get.

[PHP]
Python
>>> 1/7.0
0.14285714285714285[/PHP]

Isn't that closer?

---

### Post by Patrick01 on 2009-07-22
the solution to use % (modulus) operator. Here is full solution with C#:
 
[http://interviewpattern.com/post/Bitwise-Interview-Question-with-C.aspx](http://interviewpattern.com/post/Bitwise-Interview-Question-with-C.aspx)

---

### Post by soltanis on 2009-07-22
From the total amount of thinking I performed whilst eating 5 Ritz crackers was that 7 is close to 8 which is 2^3;

48 / 8 = 6
42 / 7 = 6
42 + 6 = 48

Hmmmm....
EDIT. Never mind.

---

### Post by wmcbrine on 2009-07-22
I can't imagine this isn't homework.

There is little or no reason to avoid straight division on a modern computer. This sort of thing made more sense in the bad old days, when the built-in division instructions in microprocessors were slow, or the worse older days, when they didn't even have them.

Gah, I just realized that this thread is two-and-a-half years old. AND homework.

---

