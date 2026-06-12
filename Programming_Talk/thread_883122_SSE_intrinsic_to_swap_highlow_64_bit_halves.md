---
title: "SSE intrinsic to swap high/low 64 bit halves?"
date: 2008-08-07
forum: Programming Talk
---

### Post by MeMooMeM on 2008-08-07
Hi!

I am new to SIMD programming. I can't find an intrinsic to swap high and low halves of a 128 bit that hold two doubles. What is the most effective way to do that?

Thank a lot in advance!

---

### Post by cszikszoy on 2008-08-07
Not sure about SIMD programming, but most hardware architectures provide support for bit rotation in assembly.  I only have assembly experience with the Motorola 68k and 68hc11, both of which have bit rotation.

In case you don't know, bit rotation is like a shift, but the bits being shifted out are shifted back in on the other side.

Not sure if that's what you are looking for.

---

### Post by MeMooMeM on 2008-08-08
> **cszikszoy said:**
> Not sure about SIMD programming, but most hardware architectures provide support for bit rotation in assembly.  I only have assembly experience with the Motorola 68k and 68hc11, both of which have bit rotation.

In case you don't know, bit rotation is like a shift, but the bits being shifted out are shifted back in on the other side.

Not sure if that's what you are looking for.

Thank you for your reply! I don't know how it is implemented and how expensive it is, but I found the following solution that uses a SSE intrinsic:

r1 = _mm_shuffle_pd(r1, r1, 1);

This applies a shuffle on the register itself, resulting in swapped 64 bit halves. This might be requiring two cycles and your bit rotation solution could be faster. I will look into it and update the thread if I find anything. Thanks again :)

---

### Post by cszikszoy on 2008-08-08
Good find.  I'm sure that one you have is better.  I was worried about the ROL and ROR assembly directives because I wasn't sure how many bits you can shift / clock cycle.

If you have that swap command I'm sure thats better.

---

