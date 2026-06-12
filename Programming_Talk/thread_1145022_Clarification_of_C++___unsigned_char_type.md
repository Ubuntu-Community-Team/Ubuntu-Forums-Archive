---
title: "Clarification of C++   unsigned char type"
date: 2009-05-01
forum: Programming Talk
---

### Post by David C. on 2009-05-01
So, I've been reading through *Teach Yourself C++*and doing the exercises. I worked one that showed how the char type works with the assignment statements. It clarified it, but as I read through the paragraph the author brings up *unsigned char* and briefly explains that char type is an *"integer 8-bit numerical type..." *but he doesn't give any clear explanation as to what an unsigned char type is or does or how it is used. The only definition given is early in the chapter where it is identified as an integer type specifier. 

Could someone provide a bit more of an explanation?

---

### Post by wmcbrine on 2009-05-01
If you're treating it as an integer, then a signed char covers the values -128..127. An unsigned char covers 0..255. That's it. It's exactly analogous to the signed/unsigned distinction for larger integers. If you're not treating the characters as integers, or doing greater-than/less-than comparisons, then it makes no difference.

I think most systems make chars signed by default, but it's not specified by the standard.

P.S. Note that ASCII falls entirely within 0..127, so you can still do comparisons with signed chars if your text is pure ASCII.

---

### Post by eye208 on 2009-05-01
> **David C. said:**
> the author brings up *unsigned char* and briefly explains that char type is an *"integer 8-bit numerical type..." *but he doesn't give any clear explanation as to what an unsigned char type is or does or how it is used.
Both signed and unsigned char are integer 8-bit numerical types, but in the signed variant the leftmost bit is used to represent the sign. If it is zero, the value is positive, otherwise negative. The result is that signed and unsigned integer types overflow/underflow at different positions:

binary 00000000 = hex 00 = unsigned 0 = signed 0
binary 00000001 = hex 01 = unsigned 1 = signed 1
binary 00000010 = hex 02 = unsigned 2 = signed 2
binary 00000011 = hex 03 = unsigned 3 = signed 3
...
binary 01111110 = hex 7E = unsigned 126 = signed 126
binary 01111111 = hex 7F = unsigned 127 = signed 127
binary 10000000 = hex 80 = unsigned 128 = signed -128 **(overflow)**
binary 10000001 = hex 81 = unsigned 129 = signed -127
...
binary 11111110 = hex FE = unsigned 254 = signed -2
binary 11111111 = hex FF = unsigned 255 = signed -1
binary 00000000 = hex 00 = unsigned 0 **(overflow)** = signed 0

Because of the differing interpretation of the leftmost bit, care is required when mixing signed and unsigned types in assignments, comparisons and conversions.

---

### Post by Can+~ on 2009-05-01
Signed Char ([FONT="Courier New"][COLOR="DeepSkyBlue"]signed char[/COLOR][/FONT])
[INDENT][COLOR="Red"]0[/COLOR]0000000 = positive
[COLOR="Red"]1[/COLOR]0000000 = negative[/INDENT]

Unsigned Char ([FONT="Courier New"][COLOR="DeepSkyBlue"]unsigned char[/COLOR][/FONT])
[INDENT]00000000 = always positive[/INDENT]

As mentioned above, both are overflowed with ease.

Oh, and you're not just limited to chars, integers and floats got sign too:

(32-bit signed integer) ([FONT="Courier New"][COLOR="DeepSkyBlue"]signed int[/COLOR][/FONT])
[INDENT][COLOR="Red"]0[/COLOR]0000000 00000000 00000000 00000000[/INDENT]

---

### Post by dwhitney67 on 2009-05-01
> **wmcbrine said:**
> ...

I think most systems make chars signed by default, but it's not specified by the standard.
...

I just learned recently that the PowerPC treats the 'regular' char as unsigned.  Using the gcc option "-fsigned-char" (or maybe it was "-fno-unsigned-char") sorted this out.

---

### Post by mkoehler on 2009-05-01
> **Can+~ said:**
> Signed Char ([FONT="Courier New"][COLOR="DeepSkyBlue"]signed char[/COLOR][/FONT])
[INDENT][COLOR="Red"]0[/COLOR]0000000 = positive
[COLOR="Red"]1[/COLOR]0000000 = negative[/INDENT]

Unsigned Char ([FONT="Courier New"][COLOR="DeepSkyBlue"]unsigned char[/COLOR][/FONT])
[INDENT]00000000 = always positive[/INDENT]

As mentioned above, both are overflowed with ease.

Oh, and you're not just limited to chars, integers and floats got sign too:

(32-bit signed integer) ([FONT="Courier New"][COLOR="DeepSkyBlue"]signed int[/COLOR][/FONT])
[INDENT][COLOR="Red"]0[/COLOR]0000000 00000000 00000000 00000000[/INDENT]

Ditto.  The easiest way to think about signed variables vs. unsigned variables is that the upper limit of a unsigned variable register is roughly twice as high as that of a signed.

For example:
- Character (8-bit) - 
2^8 = 256.  Thus, an unsigned char goes from 0 to 255 and a signed char goes from -128 to 127.

- Integer (32-bit) -
2^32 = 4294967296.  Thus, an unsigned int goes from 0 to 4294967295 and a signed int goes from -2147483648 to 2147483647.

Obviously, these are the limits for a 32-bit machine.  It's the same for a 64-bit machine, except for the fact that everything is based off of 2^64.  Good luck with learning C++ :P

---

### Post by c174 on 2009-05-03
Another thing: If you assign a 'signed char' to a 'short' you will experience "sign extension" (if the 'char' was a negative number the eigth most significant bits of the 'short' will be set to ones). So care is needed when combining two 'char's into a 'short' -- for example when taking care of big/small endianess.

---

