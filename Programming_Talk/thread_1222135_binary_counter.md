---
title: "binary counter"
date: 2009-07-24
forum: Programming Talk
---

### Post by ged25 on 2009-07-24
Could someone please tell me how to code a binary counter ?
The output should be as follows:

0, 1, 10, 11, 100, 101, 110, 111...

I don't want to take each number in decimal form and convert it into binary. I'm looking for another method of doing it.

---

### Post by MadCow108 on 2009-07-24
depends on the language. higher languages probably provide methods to print in binary.
the simplest way I can think if in c++ would be:
```

const int n=4;
bitset<n> bit(0);
for (int i=0; i<1<<n; i+=1)
{
	bit=i;
	std::cout << bit << std::endl;
}

```

unfortunatly c++ streams have no binary flag as they have for hex and octal :(

---

### Post by Can+~ on 2009-07-24
Sounds like homework.

And won't you use decimal and print as binary? That's the most basic way to operate with bits.

---

### Post by unknownPoster on 2009-07-24
> **Can+~ said:**
> Sounds like homework.

And won't you use decimal and print as binary? That's the most basic way to operate with bits.

It has to be the most straightforward way as well. I've been programming for a few years and I can't think of any other way to do it, but my knowledge of existing algorithms is a bit limited.

Heck, in Java you could just perform your decimal for loop and then on each value perform:

```


toBinaryString(value);


```

Of course this code won't work alone, but it may point you in the right direction.

---

### Post by MindSz on 2009-07-24
Off the top of my head, a nice way to do it would be to try and implement it as close to the real thing (hardware) as you can.

So you'd have to have an array of n characters (or integers or whatever you like, but you're only gonna be using 1s and 0s), where n is the max number of bits you want your adder to represent.

So for every 'clock cycle' you switch bit[0], every two cycles you switch bit[1], every 4 cycles switch bit[2], and so on ...

So you switch bit[x] every 2^x clock cycles :)

EDIT: Remember to print your array backwards so you get the LSB on the right side!

---

### Post by jpkotta on 2009-07-24
> **Can+~ said:**
> Sounds like homework.

And won't you use decimal and print as binary? That's the most basic way to operate with bits.

> **unknownPoster said:**
> It has to be the most straightforward way as well. I've been programming for a few years and I can't think of any other way to do it, but my knowledge of existing algorithms is a bit limited.

Heck, in Java you could just perform your decimal for loop and then on each value perform:

```


toBinaryString(value);


```

Of course this code won't work alone, but it may point you in the right direction.

There is no such thing as a decimal (or hex or binary or any other base) numbers.  The base refers to the *representation* of the number; the number itself is an abstract concept.  Most computers keep the internal representation as binary, but that is immaterial (when you do arithmetic on them).  Sorry to nitpick but I remember once when I was a TA, there was an exercise that involved printing out numbers in different bases, and this confused some students to no end.

Anyway, this does sound like homework.  You need to learn about bit operations.  The following syntax works for many languages, C and Python for sure.

Set nth bit of x:
```
x |= 1<<n
```
Clear nth bit of x:
```
x &= ~(1<<n)
```
Toggle nth bit of x:
```
x ^= 1<<n
```
Get nth bit of x:
```
x & (1<<n)
```

---

### Post by ged25 on 2009-07-25
Thanks for the responses. Its not a homework problem. I gave a specific instance of a general problem I was trying to solve. Looks like I gave the wrong example.

Basically what I was intending to find out was if there was a way to generate a sequence of values.

eg:

0,1,10,11,100...

0,1,2,10,11,12,20..

0,1,2,3,10,11,12,13,20.. 

etc

I wanted to know whether there was some algorithm that generated this automatically rather than trying to convert each number into the specified base.

---

### Post by jpkotta on 2009-07-25
> **ged25 said:**
> 
I wanted to know whether there was some algorithm that generated this automatically rather than trying to convert each number into the specified base.

Yes, there is a generic algorithm for this. MindSz's response is 90% there.  Just replace 2^x with base^x, and "switch" with "add modulo base".

I just did it in python, and I made a so-called ripple counter.  It increments the least significant digit by one and does carries on any digit that is > base.

---

### Post by ged25 on 2009-07-25
Thanks a lot for your help.

---

### Post by Lux Perpetua on 2009-07-25
Of course, there are algorithms. The easiest, and most enlightening, is to represent your number as a sequence of digits in your chosen base and just "increment" the sequence repeatedly. That's a lot more straightforward than dealing with clock cycles and periodicity. 

Let's choose base 5, and suppose our number is 

30444 (base five). 

To get the next number, add one to the last digit: 

30445

...except 5 isn't allowed, since it's base 5. Since the number five is actually 10 in base five, you have to replace it with 0 and carry the 1 to the next place to the left:

30450

...and do the same:

30500

...and once more:

31000

---

### Post by asbuntu on 2009-08-03
The official way to convert from one base to another is to repeatedly divide the number by the base, using the arithmetic rules for the incoming base, truncating down, until you have nothing left.  At that point, you write down the remainders in the reverse order encountered.

The hard part is remembering to do the arithmetic in the incoming base.  If you are converting from base 5 to base 3, for instance, then dividing 12 by 3 gives 2 remainder 1, not 4 remainder 0.  Also, if you going up in base, say from 5 to 10, you are dividing by 20, not by 10, because 20 in base 5 is 10 in base 10.

---

### Post by lisati on 2009-08-03
> **ged25 said:**
> Could someone please tell me how to code a binary counter ?
The output should be as follows:

0, 1, 10, 11, 100, 101, 110, 111...

I don't want to take each number in decimal form and convert it into binary. I'm looking for another method of doing it.

As you might have gathered there are multiple answers. 

Suggestion: write your binary numbers so they have the same number of digits, e.g. 000, 001, 010, 011, 100, 101, 110, 111 etc. Then ask yourself what each of the digits means, and you'll be on your way to finding a solution.

---

