---
title: "Q: Are all constants equal?"
date: 2013-05-11
forum: Programming Talk
---

### Post by seeker.k3 on 2013-05-11
Are certain constants processed more efficiently than others? For example, is a constant such 63, which is equivalent to 64 when counting from zero, preferred to a constant such as 64, because the first number (63), is 2^5. Likewise, is it more efficient to do .125^2 than to do .1^2. I know these are trivial numbers, but I'm interested to know if such a principle exists. Should I prefer numbers like 127, 255, 1023, and decimals like .0625?

Can anyone comment?
Thank you.

---

### Post by Vaphell on 2013-05-11
if you think about such optimizations by hand, forget it, generally they don't matter. It's the algorithm that makes or breaks the program, potential gains from such trivial things are in most cases hard to measure with all these GHz's.

some values lend themselves to nice low level shortcuts, eg operations of x***2^n** or x/**2^n**
it can be done with bitshifting which is a cheap operation
you simply take the bits move them to the left or right depending on if it's * or / and pad with 0s ( in C bitshift can be written as x << n, x >> n )
00[COLOR="#008000"]010100[/COLOR] * 2^[COLOR="#0000FF"]2[/COLOR] = [COLOR="#008000"]010100[/COLOR][COLOR="#0000FF"]00[/COLOR]
[COLOR="#008000"]000101[/COLOR]00 / 2^[COLOR="#0000FF"]2[/COLOR] = [COLOR="#0000FF"]00[/COLOR][COLOR="#008000"]000101[/COLOR]

generally compilers detect such constants and do optimize operations on them to the cheapest possible

floats do require some understanding because most fractions can't be represented as a fixed-length series of powers of 2 and you simply lose precision (an equivalent to the classic example of 0.99999.... = 1, cutting the infinite tail off in any place instantly makes the number =/= 1) and comparisons x == y may yield 'improper' result even if the values 'look' the same.
```
$ echo "1.0==1.0" | bc -l
1
$ echo "1.0/3*3==1.0" | bc -l     # 1.0/3*3 lost precision along the way and is not equal to 1.0
0
```
it's more about prevention of unforeseen situations than constants better than others though.  If you pick a float number, get one that can fit the whole 2^n series in the amount memory reserved for it, that's it.

---

### Post by trent.josephsen on 2013-05-11
In a hardware component like a multiplier or an adder, an operation always takes the same amount of time, regardless of what the inputs are. In some architectures this is always 1 clock cycle and on some architectures some operations take longer than others, but a (say) multiply instruction always takes as long as every other multiply instruction.

You can perform shortcuts. Multiplying by 9 can be done by shift-left-and-add without incurring the overhead of a general multiplier. On some machines this would actually be slower than just doing the multiply instruction, which is why, if you're writing in a high-level language, you should always leave this kind of microoptimization up to the compiler. If you need control on that kind of level, you should be using assembly language to begin with.

There are sometimes reasons to prefer powers of 2. If you store a number in a file and you can pack it into a specific whole number of bits, you reduce the possibility of corruption resulting in an invalid value. For instance, if you're writing a game in which the player can have any experience level from 1 to 100, you have to use 7 bits -- but then the player might edit the save file to give himself a level of 127 or 128, which might cause the game to crash. You can avoid this problem by defining valid ranges to have power-of-two sizes (like 1-64 or 0-1023), and when you write the data to long term storage, pack it into the smallest possible size (or just discard the extra bits when you read it back). But if you don't have a specific reason to do so, just pick numbers because they make sense. And don't forget to comment in the code to say why you chose the value you did.

---

### Post by shawnhcorey on 2013-05-11
**Do not optimize without profiling.**

First, get the code to work. Second, run it thru a profiler to see where it is the slowest. Third, optimize only the slowest portion of the code. Repeat from step 2 until the code is fast enough.

---

### Post by tgalati4 on 2013-05-11
It depends on the processor, the compiler, and the code that is using the constants.  With hardware-based, super-scalers--some math operations can be faster with carefully-defined constants.  Some compilers will optimize for this (depending on the optimization level selected and how good the compiler is in the first place).  Your code can help by clever writing and defining of constants and mathematical operations.  Until you specify the processor, compiler and code to be optimized, it's difficult to answer your question.

And even after all of this, you may not notice the difference in performance with modern processors.

---

### Post by seeker.k3 on 2013-05-13
Ok, that answers my question. Thanks all.

---

