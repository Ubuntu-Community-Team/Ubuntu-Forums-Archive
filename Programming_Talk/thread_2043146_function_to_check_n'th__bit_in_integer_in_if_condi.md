---
title: "function to check n'th  bit in integer in if condition"
date: 2012-08-15
forum: Programming Talk
---

### Post by 681ankit on 2012-08-15
All about GCC  .. c language code
hello , I am writing a code that needs to check the 1st and 6th bit of specific number whether it is set to 0 or not in "if" statement..
I'm writing it in following way:-

int x=63; // in binary x=111111

if( condition )
{
     .........
     ............
}


So..please tell me how can i write condition to check the 1st and 6th bit of int x..?

---

### Post by Bachstelze on 2012-08-15
We don't readily give homework help here. You need to make a honest try, and then we will help you if you get stuck.

---

### Post by 681ankit on 2012-08-16
> **Bachstelze said:**
> We don't readily give homework help here. You need to make a honest try, and then we will help you if you get stuck.

Ya ,i know you are right ..Actually I tried it ..as follows but i cant get it properly..

int x=63; // x=111111

if( x & 1<<6)
  {
     this condition will true if there is 1 at position 6
  }
else
{
   printf("zero is set at position 6th");
}

this is my code ...
But i want if condition true if there is 0 at position 6
there should not be else condition ...

..Thanks for reply

---

### Post by vexorian on 2012-08-16
It is almost as if you needed to use an operator that could turn true into false and false into true.

---

### Post by 681ankit on 2012-08-16
> **vexorian said:**
> It is almost as if you needed to use an operator that could turn true into false and false into true.

thanks...I know it was stupid question to ask but thanks for hint...I get it correctly now

---

### Post by dwhitney67 on 2012-08-16
> **681ankit said:**
> All about GCC  .. c language code
hello , I am writing a code that needs to check the 1st and 6th bit of specific number whether it is set to 0 or not in "if" statement..

So..please tell me how can i write condition to check the 1st and 6th bit of int x..?

You might consider defining a mask for the bits of interest.  When you AND your number with the mask, if the result equals your mask's value, then you know the bits are set.

For example:
```

const unsigned int mask = 0x21;    // same as binary 100001
unsigned int number = 33;

if ((number & mask) == mask)
{
    // bits are set
}
else
{
    // bits not set
}

```

---

### Post by spjackson on 2012-08-17
> **681ankit said:**
> 
if( x & 1<<6)
  {
     this condition will true if there is 1 at position 6
  }

Will it? Which position does 1<<1 test?

---

### Post by vexorian on 2012-08-17
Position 1.

Position 6 is the 7-th position. Position 1 is the second position. Position 0 is the first position.

---

### Post by dwhitney67 on 2012-08-17
> **vexorian said:**
> Position 1.

Position 6 is the 7-th position. Position 1 is the second position. Position 0 is the first position.

That's if you are counting from 0.  It wasn't clear if the OP meant that the first bit (ie the least significant bit) is bit 1, and whether the other bit of interest is five positions in front of the first.

I do agree that in the "industry", bit 0 denotes the first bit.  As from my previous example, I assumed, as you did, that the bits of interest can be denoted using the mask 0x21, which is equivalent to 00100001 in binary.

With unclear requirements, comes incomplete code.  Let's hope the OP isn't launching a rocket to the moon.

---

### Post by spjackson on 2012-08-17
> **dwhitney67 said:**
> That's if you are counting from 0.  It wasn't clear if the OP meant that the first bit (ie the least significant bit) is bit 1, and whether the other bit of interest is five positions in front of the first.

I do agree that in the "industry", bit 0 denotes the first bit.  As from my previous example, I assumed, as you did, that the bits of interest can be denoted using the mask 0x21, which is equivalent to 00100001 in binary.

With unclear requirements, comes incomplete code.  Let's hope the OP isn't launching a rocket to the moon.
I agree that it is common to refer to the LSB as the zeroth bit, but I don't think this is universal, such that "first" and "sixth" are ambiguous. The OP showed the bit representation thus:
```

int x=63; // x=111111

```i.e. showing precisely 6 bits. It seems somewhat odd to be saying here's a bit pattern but the bit I'm interested in is not in this pattern - it's one just outside the pattern.

I didn't say that the OP's assertion was wrong, just questioned it for the above reasons.

---

### Post by ofnuts on 2012-08-17
> **spjackson said:**
> I agree that it is common to refer to the LSB as the zeroth bit, but I don't think this is universal, such that "first" and "sixth" are ambiguous.
The LSB is bit 0, that that makes it the first bit :)

---

### Post by vexorian on 2012-08-17
> **dwhitney67 said:**
> That's if you are counting from 0.  It wasn't clear if the OP meant that the first bit (ie the least significant bit) is bit 1, and whether the other bit of interest is five positions in front of the first.

I do agree that in the "industry", bit 0 denotes the first bit.  As from my previous example, I assumed, as you did, that the bits of interest can be denoted using the mask 0x21, which is equivalent to 00100001 in binary.

With unclear requirements, comes incomplete code.  Let's hope the OP isn't launching a rocket to the moon.
When coding in C's, you are always counting from 0. It is after all a 0-indexed language.

Anyway, it was the OP's who came up with the bit shift code and called 1<<6 position 6, so I just adopted the OP's own indexing.

---

