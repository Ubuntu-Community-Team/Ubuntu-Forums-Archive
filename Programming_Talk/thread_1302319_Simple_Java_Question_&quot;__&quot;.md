---
title: "Simple Java Question &quot; | &quot;"
date: 2009-10-26
forum: Programming Talk
---

### Post by UndefinedMind on 2009-10-26
Simple code:
```
int f = 48, g = 16;
System.out.print( f | g );
```

The answer is 48, but I have no clue what the '|' operation does. Scrub question, but I've already googled with no success.

---

### Post by Reiger on 2009-10-27
It is the &#8216;bitwise or&#8217;. In order to see what it does you must first convert the operands (48 and 16 in your case) to binary:

110000 = 48
010000 = 16
------------ |
110000 = 48

Another example:

110000 = 48
010011 = 19
------------ |
110011 = 51

---

### Post by UndefinedMind on 2009-10-27
So, if that column contains a 1, the answer has a 1 in that spot, with a 0 being only if both columns have a 0?

---

### Post by NovaAesa on 2009-10-27
> **UndefinedMind said:**
> So, if that column contains a 1, the answer has a 1 in that spot, with a 0 being only if both columns have a 0?

Correct. I have never used it though. It might be useful when trying to optimize something maybe?

---

### Post by UndefinedMind on 2009-10-27
I understand now, thank you both.
This was a multiple choice question, it didn't give an example, just that bit of code.

[quote=Wikipedia.org]
Bitwise operations are necessary for much low-level programming, such as writing device drivers, low-level graphics, communications protocol packet assembly and decoding.
 Although machines often have efficient built-in instructions for performing arithmetic and logical operations, in fact all these operations can be performed just by combining the bitwise operators and zero-testing in various ways.
 For example, here is a [pseudocode]("http://en.wikipedia.org/wiki/Pseudocode") example showing how to multiply two arbitrary integers a and b (a less than b) using only bitshifts and addition:

 c := 0
**while** b != 0
    **if** (b **and** 1) != 0
        c := c + a
    shift a left by one
    shift b right by one
 
**return** c[/quote]

---

### Post by Reiger on 2009-10-27
This kind of thing (bit manipulation) is typically useful for specifying cumulative bitmasks (i.e.: function(params, A_FLAG | ANOTHER_FLAG) ) as well as constructing values in binary file formats.

Bit-wise & for instance is very useful when converting unsigned bytes to integers because casting the byte value 0xFF to (signed) integer results in 0xFFFFFFFF (-1) -- and you want 0x000000FF (255). The bitwise & operation can fix that easily: int value = ((int) byteValue) & 0xFF.

Bit shifts combined with bit-wise or is very useful when packing multiple byte values into an int; furthermore, bit shifts occur in closed form solutions of the &#8216;Josephus problem&#8217;.

---

### Post by Arndt on 2009-10-27
> **UndefinedMind said:**
> Simple code:
```
int f = 48, g = 16;
System.out.print( f | g );
```

The answer is 48, but I have no clue what the '|' operation does. Scrub question, but I've already googled with no success.

Try googling for "java operator".

---

