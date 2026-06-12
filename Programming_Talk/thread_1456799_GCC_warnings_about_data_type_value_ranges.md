---
title: "GCC warnings about data type value ranges"
date: 2010-04-17
forum: Programming Talk
---

### Post by MacUntu on 2010-04-17
I've written a small example to understand data types in C (compiled with -Wall):

```
int main(void)
{
    [COLOR="Blue"]/* no warning */[/COLOR]
    short int r = 32768;
    [COLOR="Blue"]/* overflow in implicit constant conversion */[/COLOR]
    short int s = -32769;
    [COLOR="Blue"]/* large integer implicitly truncated to unsigned type */[/COLOR]
    unsigned short int t = 65536;
    [COLOR="Blue"]/* no warning */[/COLOR]
    unsigned short int u = -1;
    
    return 0;
}
```

Basically I don't understand the two cases where I get no warnings. I fail to see how cases 1 & 3 and 2 & 4 differ. Any ideas?

---

### Post by falconindy on 2010-04-17
I could be mistaken, here but... Whole number literals are assumed to be of type int. If you use a cast in your third example, the compiler shuts up. 

In the 4th case, -1 can be adequately represented by an unsigned short int, even though if you try to print it, it won't be displayed as -1. Again, if you cast it as an unsigned short int, **then** you get the proper warning about overflow.

---

### Post by lisati on 2010-04-17
A quick moment's reflection, I might be mistaken:

The second one: -32767
The third: 65535

---

### Post by MadCow108 on 2010-04-17
the difference between 1 & 3 and 2& 4 are that in the first case the number can be represented in 16 bits, the compiler assumes the programmer knows which representation is used and thus the result of that assignment (pretty optimistic in my opinion ;) ).
In the other case the value does not fit into 16 bit, so that is almost always an error and the compiler can safely warn.

the optimistic behavior in the forth case can even be be motivated:
many programmers think thats a valid way to receive an int with all bits set
but this relies on twos complement like representation of integers

the correct way would be ~0

but so many people use the -1 "trick" it would create loads of warnings in existing projects and twos complement is used on most architectures (especially x86). So the decision was made not to warn.

---

### Post by falconindy on 2010-04-17
> **lisati said:**
> A quick moment's reflection, I might be mistaken:

The second one: -32767
The third: 65535

I think the point was to explicitly overflow the data type, the OP was "correct" in his assignments.

---

### Post by MadCow108 on 2010-04-17
btw you can get warnings in all cases with the -Wconversion flag.

but unfortunately that also warns in case of many function prototype mismatches which even I don't understand and also do no harm.
Sadly this makes that warning flag quite useless.
(speaking of gcc 4.1 I recall reading it was changed in newer gcc versions but I never tested it)

---

### Post by lisati on 2010-04-17
> **falconindy said:**
> I think the point was to explicitly overflow the data type, the OP was "correct" in his assignments.

Acknowledged. :)

---

### Post by MacUntu on 2010-04-17
Thanks for your answers, guys! I'm still not totally happy but -Wconversion is a good start. Seems I need to dig more into GCC's docu. :P

> **falconindy said:**
> if you cast it as an unsigned short int, **then** you get the proper warning about overflow.

An explicit cast is something forced by the programmer - I don't expect to see a warning in that case and actually GCC doesn't complain. :)

---

