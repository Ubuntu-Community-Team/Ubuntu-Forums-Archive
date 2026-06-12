---
title: "Bitwise operators in C++"
date: 2008-08-29
forum: Programming Talk
---

### Post by StOoZ on 2008-08-29
im kinda new to C++ , using it for 6 months now , been reading some books about it , and STL , and using it very intensively for the last two months in a project im doing , with several other libs except from the standard and STL (such as wxwidgets ,etc..) , now I wonder , why should I read && learn about bitwise operators? when do they come handy?
I find that subject pretty obscured.

---

### Post by babounours on 2008-08-29
some guys are programming your drivers or doing math with C. bitwise operators come handy with memory addresses when dealing with masques for exemple. like for IP addressing

---

### Post by monkeyking on 2008-08-29
You shouldn't read and learn how to use bitwise operators.
I think for most users, they are the last thing they will ever need.

---

### Post by crdlb on 2008-08-29
There is only one usage of bitwise operators that you need outside of extremely lowlevel stuff: storing multiple booleans in a single integer. You don't really need to know exactly how this works, but you do need to be able to recognize and use it. 
```

enum {
    FRUIT_APPLE = 1 << 0,
    FRUIT_PEAR = 1 << 1,
    FRUIT_ORANGE = 1 << 2
} FruitFlags;

fruit_set_allowed (FruitFlags allowed_fruit);

```

You can call fruit_set_allowed, allowing apples and pears by using ```
FRUIT_APPLE | FRUIT PEAR // bitwise or
```
And you can test allowed_fruit for apples with ```
if (allowed_fruit & FRUIT_APPLE) // bitwise and
```

This is extremely common in C APIs because you can add another entry (e.g. FRUIT_BANANA) without changing the function's signature. C++ has plenty of ways around it, but you'll still run into them.

---

### Post by samjh on 2008-08-30
> **StOoZ said:**
> im kinda new to C++ , using it for 6 months now , been reading some books about it , and STL , and using it very intensively for the last two months in a project im doing , with several other libs except from the standard and STL (such as wxwidgets ,etc..) , now I wonder , why should I read && learn about bitwise operators? when do they come handy?
I find that subject pretty obscured.

I've used bitwise operators for file compression, data encoding/decoding, and serial communications.

There would be other uses as well.

---

### Post by mike_g on 2008-08-30
This function does 32 bit colour blending in software with a lot of bit manipluation:
```
Uint32 ColourBlend(Uint32 rgb_1, Uint32 rgb_2, Uint16 alpha_1)
{
    Uint16 alpha_2 = 256 - alpha_1;
    Uint32 rb_1 = ((rgb_1 & 0x00FF00FF) * alpha_1) & 0xFF00FF00;
    Uint32 g_1  = ((rgb_1 & 0x0000FF00) * alpha_1) & 0x00FF0000;
    Uint32 rb_2 = ((rgb_2 & 0x00FF00FF) * alpha_2) & 0xFF00FF00;
    Uint32 g_2  = ((rgb_2 & 0x0000FF00) * alpha_2) & 0x00FF0000;
    return ((rb_1+rb_2) | (g_1+g2)) >> 8;
}
```
Just another use for it.

---

### Post by cszikszoy on 2008-08-30
> **StOoZ said:**
> && 
I find that subject pretty obscured.

&& is logical, not bitwise :)

---

### Post by monkeyking on 2008-08-30
> **StOoZ said:**
> ... why should I read && learn about ..


The && referrers back the the read AND learn, in his sentence.

not the c/c++ operator

---

### Post by cszikszoy on 2008-08-30
> **monkeyking said:**
> The && referrers back the the read AND learn, in his sentence.

not the c/c++ operator

I know that... it was a joke, hence the :)


:)

---

### Post by monkeyking on 2008-08-30
hmm,ok let's forget this one then...

---

### Post by StOoZ on 2008-08-30
> **cszikszoy said:**
> I know that... it was a joke, hence the :)


:)

heheh ... meant AND ... like :
if (x && y) {...}

---

