---
title: "[c++] bitwise operators and if statement"
date: 2009-08-10
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-08-10
I thought I understood the basics of bitwise operators but I don't.
Here's my problem. I want to check if a "flag" variable is set. I don't know how to do it. All I came up with is this:
[php]if ((flags & G_PARAM_WRITABLE) == true)[/php]
This never gets called although I know the flag is set.
[php]if ((flags & G_PARAM_WRITABLE) == false)[/php]
This works when it should.

G_PARAM_WRITABLE = 1 << 1

How do I check if this specific flag is set or not in an if statement?

thank you.

---

### Post by Sockerdrickan on 2009-08-10
[php]#include <iostream>

int main() {
    enum Test{LOL=1,ROFL=2,FOO=4,BAR=8};
    int foo;

    foo|=ROFL;

    if(foo & ROFL)
        std::cout<<"lol"<<std::endl;
}[/php]Just a note:
[COLOR=#000000][COLOR=#007700][php]//lol[/php][/COLOR][/COLOR]

---

### Post by SledgeHammer_999 on 2009-08-10
Yeah I knew that... but something strange happens when I do **if (flags & G_PARAM_WRITABLE)**. It works. But why?

---

### Post by Sockerdrickan on 2009-08-10
& checks if G_PARAM_WRITABLE bit is set

---

### Post by SledgeHammer_999 on 2009-08-10
I know, but shouldn't both
[php]if ((flags & G_PARAM_WRITABLE) == true)[/php]
and
[php]if (flags & G_PARAM_WRITABLE)[/php]
be equal?

---

### Post by Sockerdrickan on 2009-08-10
I don't do much bitwise manipulation but logically those look the same.

edit: actually there is a comparison going on of the bits of "true" probably... lol

---

### Post by Habbit on 2009-08-10
The problem is that the result of (int & int) is int. When you try to compare that as equal to "true", which is an integral constant of type "bool", the type system promotes that second operant to int, with a value that will most likely be 0x00000001. If your flag is not in the first bit, the two bit patterns differ and the int==int comparison will fail, thus your apparently corect "if ((int  & int) == true)" test fail.

However, when you do a plain "if (int & int)" comparison, the int result is "casted" (not actually, but you get the idea) to a boolean value using the rule "zero->false, nonzero->true", and you get the cookie :KS

This is one of the many evil side effects of "bool" being considered a 1-bit integral type.

---

### Post by dwhitney67 on 2009-08-10
> **SledgeHammer_999 said:**
> Yeah I knew that... but something strange happens when I do **if (flags & G_PARAM_WRITABLE)**. It works. But why?

Have you had any course in either Discrete Mathematics, Logic Design, or even Comp Sci 101?

The operation you are performing is known as the AND-ing of a value using a bit mask.

If the value contains the number 5, which in binary is %101, and your mask is say, equal to 4, which in binary is %100, then when you mask the value, the result is "true" because it will be non-zero.

Here's some example bit-wise operations that can be performed.
```

Value      1 0 1
Mask       1 0 0
-----------------
AND        1 0 0
OR         1 0 1
XOR        0 0 1


Value      1 0 1
Mask       0 0 1
-----------------
AND        0 0 1
OR         1 0 1
XOR        1 0 0

```
When defining more than one mask, ensure that their bits do not overlap.  For example, in the code provide by Tuxor, he defined his masks correctly.  Unfortunately in C and C++, the usage of binary values in code has not been accepted by ISO, thus he opted for decimal values.  One could just as easily chose to use hex values, and oftentimes developers do.

---

### Post by SledgeHammer_999 on 2009-08-10
> **Habbit said:**
> The problem is that the result of (int & int) is int. When you try to compare that as equal to "true", which is an integral constant of type "bool", the type system promotes that second operant to int, with a value that will most likely be 0x00000001. If your flag is not in the first bit, the two bit patterns differ and the int==int comparison will fail, thus your apparently corect "if ((int  & int) == true)" test fail.

However, when you do a plain "if (int & int)" comparison, the int result is "casted" (not actually, but you get the idea) to a boolean value using the rule "zero->false, nonzero->true", and you get the cookie :KS

This is one of the many evil side effects of "bool" being considered a 1-bit integral type.

That makes a lot of sense now.

[quote=dwhitney67]Have you had any course in either Discrete Mathematics, Logic Design, or even Comp Sci 101?[/quote]

(I don't know what is the equivalent name in my native language). I think not. I am a hobbyist programmer.

Thank you all.

---

### Post by scourge on 2009-08-10
> **Tux0r said:**
> Just a note:
[COLOR=#000000][COLOR=#007700][php]if ((flags & G_PARAM_WRITABLE) == true)[/php]is the same as
[php]if (flags & G_PARAM_WRITABLE)[/php][/COLOR][/COLOR]

That's not true at all, so maybe you should edit that to not confuse the noobs.

```
if (flags & G_PARAM_WRITABLE)
```
is the same as
```
if ((flags & G_PARAM_WRITABLE) != 0)
```
...and "!= 0" is NOT the same as "== true".

---

### Post by Can+~ on 2009-08-11
(@scourge) Yeah. true is defined somewhere as... 1.

So when you do

(8-bit integers because I'm lazy)
```
00010101 == 00000001 yields false
```

And without the true equality:
```
00010101 != 00000000 yields true
```

The common approach on doing bitwise operations to get "flags" is:

Do you want to set an specific bit to true?

```
x |= 8

Under the hood:
xxxxxxxx
00001000 |
--------
xxxx1xxx
```

Do you want to check if it's true?


```
if (x & mask)

Under the hood:
xxxx1xxx
00001000
--------
00001000 (distinct from zero, it's true)

if (x & mask2)
xxxx1xxx
01000100 &
--------
00000000 (false) 
```

---

