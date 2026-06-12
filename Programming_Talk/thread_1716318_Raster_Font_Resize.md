---
title: "Raster Font Resize"
date: 2011-03-28
forum: Programming Talk
---

### Post by roadkillguy on 2011-03-28
So I have a font that I made with graph paper and hexadecimal numbers.  The problem is, it's not quite big enough.  I need it to be twice the size that it is now.

Is there an algorithm that turns '1100' into '11110000' or '1010' into '11001100'?  I haven't been able to think of anything yet.

---

### Post by roadkillguy on 2011-03-28
Alright, that was kind of dumb of me.  Bitwise operators are usefull here.

Here's what I used:
```
int num = 0xF0;
int num2 = 0x0000;
int i;

for(i = 0;i < 8;i ++)
{
	if((num & (0x01 << i)) >> i)
	{
		num2 |= (3 << i*2);
	}
}
```

---

### Post by VernonA on 2011-03-28
How about:
```
for (num2 = 0; num1 > 0; num1 >>= 1, num2 <<= 2)
{
    if (num1 & 1) num2 |= 3;
}

```The trouble is that this will produce a blocky-looking font, as every pixel becomes a 2x2 square. If you use a decent font manager app you can get the font scaled using smarter algorithms that will do some measure of anti-aliasing for you.
Rgds
Vernon

---

### Post by roadkillguy on 2011-03-28
I'm actually going for the hard-resize.  I'm not exactly following how your algorithm works though..

---

### Post by VernonA on 2011-03-28
Its basically the same as yours, but I just rejigged it slightly to look a bit more efficient. Most obviously rather than scan up num1 looking for bits, I keep right-shifting num1 down and then looking at what appears in bit 1 (that's the "num1 & 1" check). The loop stops when there are no more bits in num1, which is more robust than checking the bottom 8 bits in that (a) it stops early when the bits run out, and (b) it will also handle 16-bit values without modification.
Its classic C, terse and unreadable until you've been doing it a few decades!

---

### Post by roadkillguy on 2011-03-28
That's pretty nifty.

Slightly off topic, and I realize it's a stupid question, but is there a way to optimize filling in tens of thousands of floats in an array?  Many of the values are already set to the same thing they would be set to, and it seems to me like it's overkill to always be setting them.

---

### Post by VernonA on 2011-03-29
It depends on the specific situation, and in your case its unlikely you need to worry about it. Initializing a big array on a modern PC is not normally a bottleneck since setting thousands of values can be done in a fraction of a second. For truly massive arrays with many millions of values, you might consider using a bit of assembler to speed the process up, but gcc is a good compiler and will produce almost perfect code for this task anyway.
One thing that is always true though - the best way to speed up some code is to design it better. If you are finding floats are slowing you down, look at fixed point integers instead. If you need to keep scanning a massive array looking for things, consider indexing it. If the array contains, say, sampled data values, consider fitting a smoothed curve to them so you only need store a few polynomial coefficients. As I say, optimization depends heavily on the specific situation you have, and the best solution will almost always be to think of a lateral solution to the problem.

---

