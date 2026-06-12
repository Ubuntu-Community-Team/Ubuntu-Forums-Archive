---
title: "Bitwise &amp; operator"
date: 2011-02-08
forum: Programming Talk
---

### Post by SteelCore on 2011-02-08
In C, if *value* was an int type (2 bytes)

```
value = value & OxFF;
```
 
would this statement change the rightmost or leftmost 8 bits into zeros or would it change all the 16 bits of *value* into zeros.
Thank you for your help and patience.

---

### Post by schauerlich on 2011-02-08
Instead of doing your homework for you, here's a relevant wikipedia link.

[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

---

### Post by worksofcraft on 2011-02-08
> **SteelCore said:**
> In C, if *value* was an int type (2 bytes)

```
value = value & OxFF;
```
 
would this statement change the rightmost or leftmost 8 bits into zeros or would it change all the 16 bits of *value* into zeros.
Thank you for your help and patience.

"int" on my computer is 4 bytes, not 2 and I'm not sure which bits to consider as being "left" and which ones "right"? Oh... actually according to Murphy's law it will be the wrong bits that get cleared either way... so in fact it's all of them except the least significant 8 bits, but then we still don't know if they are going to be in the first byte or the last byte, let alone left or right :shock:

---

### Post by SteelCore on 2011-02-08
> **schauerlich said:**
> Instead of doing your homework for you, here's a relevant wikipedia link.

[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)

This is not for my 'homework' and your answer isn't of any measurable help.

---

### Post by SteelCore on 2011-02-08
> **worksofcraft said:**
> "int" on my computer is 4 bytes, not 2 

Sorry, that was my mistake.
I think the 8 bits of 0xFF will be aligned with the rightmost (least significant) bit of the 32 bit 'value' but will the rest of the bits be padded with zeros or they just get ignored during the ANDing??

---

### Post by worksofcraft on 2011-02-08
> **SteelCore said:**
> Sorry, that was my mistake.
I think the 8 bits of 0xFF will be aligned with the rightmost (least significant) bit of the 32 bit 'value' but will the rest of the bits be padded with zeros or they just get ignored during the ANDing??

The "and" operation is defined as setting the resulting bits to zero unless they are one in both arguments.

What you need to realize is that inside the processor there are **always** 32 bits in ALL ints and ALL of those bits will be subjected to the "and" operation. Thus making the most significant bits become zero.

It is just the output "print" method that does normally not print leading zeros on numbers (*).

p.s. you can copy and compile this little program that shows how to make print display all the leading zeros:
[php]
// gcc leading0.c
#include <stdio.h>

int main() {
	int value = 0x12345678;
	value = value & 0xFF;
	return !printf("value=%08X\n", value);
}
[/php]

```

$ gcc leading0.c
$ ./a.out
value=00000078

```


* p.s. and the compiler input that isn't forcing you to type them all in that value 0x000000FF

---

### Post by SteelCore on 2011-02-08
Understood. Using 0xFF and 0x000000FF had exactly the same effect. So in the code
```
value = value & OxFF;
```
the leftmost 8 bits of *value* would be preserved and the rest (24 bits) would be zeroed (ANDed by zeros), not ignored. Thanks again.

---

### Post by trent.josephsen on 2011-02-08
> **SteelCore said:**
> Understood. Using 0xFF and 0x000000FF had exactly the same effect. So in the code
```
value = value & OxFF;
```
the leftmost 8 bits of *value* would be preserved and the rest (24 bits) would be zeroed (ANDed by zeros), not ignored. Thanks again.
Leftmost?

---

### Post by worksofcraft on 2011-02-08
> **trent.josephsen said:**
> Leftmost?

Perhaps he is from a bigendian locale where numbers are written most significant bit first but rendered right to left? It's a good thing he isn't Chinese or we would be talking about top and bottom bits and I would then be really confused :confused:

---

### Post by Vaphell on 2011-02-08
yes, leftmost - for unothodox definitions of 'left' :)

---

### Post by SteelCore on 2011-02-08
> **trent.josephsen said:**
> Leftmost?

Thinking at the bit level does confuse. I meant rightmost.:D

---

### Post by Milliways on 2011-02-08
> **SteelCore said:**
> Thinking at the bit level does confuse. I meant rightmost.:D

In fact both are probably wrong. If you are using an Intel processor it may be bits in the middle.

This is a red herring. It is better to think of these as the Least Significant bits, then the underlying architecture is irrelevant.

I suspect you really meant the right bits as written, but it is still better to get in the habit of thinking MS LS.

---

### Post by worksofcraft on 2011-02-08
> **Milliways said:**
> In fact both are probably wrong. If you are using an Intel processor it may be bits in the middle.

This is a red herring. It is better to think of these as the Least Significant bits, then the underlying architecture is irrelevant.

I suspect you really meant the right bits as written, but it is still better to get in the habit of thinking MS LS.

Yep Milliways is right... oh no I better say "not wrong".

Anyway that's a great restaurant Milliways has... I've dined there quite a few times :)

---

### Post by SteelCore on 2011-02-09
> **Milliways said:**
> I suspect you really meant the right bits as written
Indeed this is what I actually meant
>  but it is still better to get in the habit of thinking MS LS.
I'll take note of this advice for my future readings. Thanks.

---

