---
title: "[C] Cleaning up floating point numbers when printing"
date: 2010-02-10
forum: Programming Talk
---

### Post by durand on 2010-02-10
Hi,

I have a set of floating points which I need to print to screen. How do I make sure that the numbers are neatly displayed with only the minimum number of 0s. For example, If I have 0 as a float, when I print it, I get something like 0.0000000. If I have 2.334, it prints as 2.3340000. How do I neaten up the final value so that it doesn't contain unnecessary 0s? I'd rather you pointed me in the right direction than gave me the answer straight away but I can't find much at all on this topic with google.

Thanks.

---

### Post by lisati on 2010-02-10
Which language? C & C++ allow for specifiying widths etc when you are using printf & [sprintf]("http://www.cplusplus.com/reference/clibrary/cstdio/sprintf/")

---

### Post by durand on 2010-02-10
C. I know a bit about specifying widths but I need something versatile enough that it shortens 2.30000000 to 2.3 as well as making 2.33333300 shorten to 2.333333. The width isn't the problem, the number of unneeded zeros are. In python, I would probably convert it to a string and loop remove the zeros from the end. I'm not sure what the C equivalent is.

---

### Post by dwhitney67 on 2010-02-10
Here's a webpage that discusses everything you could possibly want to know about printf() formatting.
[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

In your case, you need to decide how many digits past the decimal point you want to display.

---

### Post by durand on 2010-02-11
Oh. So there's no way of getting C to decide? I might resort to some string manipulation.
Thanks for your responses!

---

### Post by dwhitney67 on 2010-02-11
> **durand said:**
> Oh. So there's no way of getting C to decide? I might resort to some string manipulation.
Thanks for your responses!

You can perform the rounding and at the same time adjust the precision of the floating point number using code, but it does not make sense to do this unless you are asking about a homework assignment...

---

### Post by jim_24601 on 2010-02-11
Use the %g format specifier instead of %f.

---

### Post by MadCow108 on 2010-02-11
> **durand said:**
> Oh. So there's no way of getting C to decide? I might resort to some string manipulation.
Thanks for your responses!

a cstring generated at runtime is perfectly valid argument to printf
or what do you mean with "getting C to decide"?

---

### Post by durand on 2010-02-11
Well, I don't want it to lose any precision, just to remove all the pointless zeros it displays. I need C to decide on how many numbers it includes after the decimal point, without me giving it a specific amount. I'll try using strings and see if it works.

---

### Post by Some Penguin on 2010-02-11
You were already told the answer -- no experimentation is required.  You would have had the answer in minutes instead of hours if you actually read the printf() man page.

---

### Post by durand on 2010-02-11
> **Some Penguin said:**
> You were already told the answer -- no experimentation is required.  You would have had the answer in minutes instead of hours if you actually read the printf() man page.

I have read it and I can't find what I need.

---

### Post by Some Penguin on 2010-02-11
> **durand said:**
> I have read it and I can't find what I need.

Then re-read it, because it's there.  It was also already posted in this thread.

---

### Post by durand on 2010-02-11
Oh right, %g. Well, I tried it and it seems to be what I want. Thanks. However, it's messing up when it comes to simplifying 0s. Eg:
```

This program will calculate the roots of a quadratic equation with form ax² + bx + c = 0
Please enter a value for a: 1
Please enter a value for b: 2
Please enter a value for c: 1

The roots of the quadratic equation 1x² + 2x + 1 = 0 are: 
1) -1 + 1.96747e-153i
2) -1 - 1.96747e-153i

```

The last bit should be 0i...

(This is with %lg btw, I'm using doubles rather than floats.)

---

### Post by Some Penguin on 2010-02-11
Welcome to the world of limited-precision arithmetic, where things that clearly should be zero aren't exactly.  For dealing with this, it's not a bad idea to have a normalization routine that rounds to the nearest 10^-6 or so (depending on your desired level of precision) -- although with complex numbers, you need to apply this to the individual components.

Forgetting about this can really cause problems implementing numerical algorithms, as stuff that will provably converge at a certain rate in pure mathematics may end up not converging because of the approximations used by the machine.

---

### Post by durand on 2010-02-11
Hmm, thanks for the advice. I guess I'm just really suprised about how minimalist C is compared to python but that is to be expected really.

---

### Post by lisati on 2010-02-11
> **Some Penguin said:**
> Welcome to the world of limited-precision arithmetic, where things that clearly should be zero aren't exactly.  For dealing with this, it's not a bad idea to have a normalization routine that rounds to the nearest 10^-6 or so (depending on your desired level of precision) -- although with complex numbers, you need to apply this to the individual components.

Forgetting about this can really cause problems implementing numerical algorithms, as stuff that will provably converge at a certain rate in pure mathematics may end up not converging because of the approximations used by the machine.

This takes me back to my student days - more years ago than I sometimes care to remember. One of the topics covered on the courses I was on was estimates of errors and how they can propogate when results are passed through several sets of calculations. It might not make much of a difference in the examples used in homework assignments, but it's still useful to be aware of these things.

---

### Post by durand on 2010-02-11
Does this affect C++ as well? I'm thinking that that will be a more useful language for me to use when I need optimised code, rather than C.

---

### Post by Some Penguin on 2010-02-11
There are almost certainly some nice arbitrary-precision arithmetic libraries for C that may help alleviate these issues with some penalty (having to use routines written for those types rather than the standard C library routines, for instance; likely to be slower and more space-hungry as well).

But C by itself is normally using native types as much as possible, and doubles and floats use IEEE floating-point representations -- which having a finite and fixed number of bits cannot possibly enumerate the (infinite) number of values within any given range.   Some numbers simply have to be approximated, and arithmetic tends to compound the approximations.   If you add an extremely tiny number to an extremely large number, for instance, the result may not be what you want.

Something else to keep in mind is that these computations aren't necessarily reproducible exactly across platforms.  For people writing networked games with heavy use of floating-point arithmetic, one would probably want to ensure that all machines use the same approximations or at least that the deviations don't accumulate into something wildly out of synch.


Edit:  yes to C++ as well.  Same reasons.

---

### Post by durand on 2010-02-11
Mmmm, seems like quite a big problem. My main use would probably be in astrophysics computer modelling but that won't be for a few years so hopefully I get enough practise with C/C++ to recognise these problems.

---

