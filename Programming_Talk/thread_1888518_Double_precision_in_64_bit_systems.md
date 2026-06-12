---
title: "Double precision in 64 bit systems"
date: 2011-11-29
forum: Programming Talk
---

### Post by Dirich on 2011-11-29
Shouldn't a double in a 64 bit system be 128bit (at the very least when it's on a "64-bit" hardware)?

I don't know if I lack an option in the compiler (gcc) or what, but it seems that the sizeof(int) is 4 and sizeof(double) is 8. Which is what I'd expect in the 32 bit age.

Sadly when I look around for the matter I'm overflown with long double and similar stuff. I would very much like to avoid the long double type in favor of the standard double.
Do you know anything that can shed light over how to get my "64 bit" to properly work when I write code in C and compile via gcc (I use blas, llapack and I will soon try to include some cuda code into my programs, that's why I'd like to avoid long double).

Thanks!

---

### Post by ehmicky on 2011-11-29
> **Dirich said:**
> Shouldn't a double in a 64 bit system be 128bit (at the very least when it's on a "64-bit" hardware)?
A double in C on a x86_64 platform is 64 bits on most platforms : check out for example the [Linux x86_64 ABI]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&sqi=2&ved=0CB4QFjAA&url=http%3A%2F%2Fwww.x86-64.org%2Fdocumentation%2Fabi.pdf&ei=vz7VTpizHc358QOu-PGnAg&usg=AFQjCNHM5xtL4RVMdUxJSuuXe3SA6m9JEA"), page 12. I think long double is just required by the standard to be >= double, but I guess most of the time it's stored in a 128-bits format, but actually just use 80 of them, although it seems it might be on some platforms use all of them, or also only be the same as a double.
I think about the sizes of types in C :
  - the AMD64 or Intel64 specification (and I checked) doesn't say anything about it, since it doesn't care about any programming language (apart from assembly)
  - the C standard(s) only requires minimal sizes, but doesn't explicitly state the actual size of any type (it's implementation-defined), apart from char, which is always one byte-wide.
  - the x86_64 ABI of your platform may require a specific size for most types
  - some (rogue) compilers might break the rule

---

### Post by lswb on 2011-11-29
EDIT: Moderator, please remove this post!!

---

### Post by Bachstelze on 2011-11-29
> **Dirich said:**
> Shouldn't a double in a 64 bit system be 128bit (at the very least when it's on a "64-bit" hardware)?

No. Double is 64 bits, period.

[http://en.wikipedia.org/wiki/IEEE_floating-point_standard#Basic_formats](http://en.wikipedia.org/wiki/IEEE_floating-point_standard#Basic_formats)

(Even though nothing in the C standard requires following the IEEE 754 standard, not doing so would be extremely stupid.)

*EDIT:* So do not rely on double being any specific width, because sadly there are a lot of stupid compilers around, but don't expect to see 128-bit doubles any time this decade either.

---

### Post by trent.josephsen on 2011-11-29
May I ask what exactly is the problem with using double as it's defined?  I mean, there aren't many applications that demand greater precision or range than a 64 bit double can provide.

I only ask because people often worry about ranges and sizes in C when they shouldn't.  As with most type-size-related C questions, the answer is probably "Don't worry about it."

---

### Post by Dirich on 2011-11-30
> **trent.josephsen said:**
> May I ask what exactly is the problem with using double as it's defined?  I mean, there aren't many applications that demand greater precision or range than a 64 bit double can provide.

I only ask because people often worry about ranges and sizes in C when they shouldn't.  As with most type-size-related C questions, the answer is probably "Don't worry about it."

I wrote a program that uses Green's functions and, by performing renormalization-reduction procedures, computes various physical properties of a system. I also wrote a "checking" program that evaluates the analytical solution that I computed by hand (for a system of really small dimension) which I use to establish the precision of my first program.

The two programs have the very same output (I can tune the precision by some order of magnitude, it is in the range e-6 to e-9), besides for a very specific point where there is a discontinuity (the other discontinuities are fine). I also have to zoom by a factor e4 in order to actually "see" the problem arise (but I am interested in zoom of that kind in certain points).

EDIT: I included the results of the plots to give you the idea of what's happening. A picture is worth a thousand words.

A second aspect of the problem is that, even when I do not watch that specific point, there are a couple of other points (2 in a thousand nearly), where the precision of the computed Green's function, just for what concerns the imaginary part of the complex number, drops to e-3, which is not good at all (although this is a minor problem).

In other words: I do really have a numerical problem, and I do really need to "solve" it. Even if manifests only when I have a discontinuity in the points 1 and/or -1 (as far as I know :/ ).

Problem is that I would really much like to avoid extended precision (of which I just know the name, I don't even know if it exists in C, I'm trying everything else before) and long double because I use libraries (blas and lapack) and I don't remember seeing anything for types bigger than double). If I can't have a double I have to mess with the make options of the libraries (of which I know nothing) or to switch libraries (if I find some supporting bigger types), but the "best" one for me to use are those I'm using at the moment. :(

---

### Post by 11jmb on 2011-11-30
You can use GMP to create variables with arbitrarily high precision

[http://gmplib.org/](http://gmplib.org/)

---

### Post by Dirich on 2011-11-30
> **11jmb said:**
> You can use GMP to create variables with arbitrarily high precision

[http://gmplib.org/](http://gmplib.org/)

Thanks for the info. I actually found [http://mplapack.sourceforge.net/](http://mplapack.sourceforge.net/) that is based on GMP and QD and reproduces BLAS and LAPACK packages.

The only thing left is for me to understand what's the meaning of all this "64-bit" foolishness... What is exactly "64" bit when the word is still 32?
What changed from when hardware and software were 32 bit?

---

### Post by trent.josephsen on 2011-11-30
Okay, I apologize for being skeptical of the need for high precision.

> The only thing left is for me to understand what's the meaning of all this "64-bit" foolishness... What is exactly "64" bit when the word is still 32?
What changed from when hardware and software were 32 bit?
The number of addressable memory locations and the size of the largest number the ALU or floating-point coprocessor can handle.

(Most 64 bit machines do indeed have a 64 bit word size.  The significance of that diminishes greatly, however, when the word is not the smallest addressable chunk of memory.  For example, on a 64 bit system, float may be 32 bit, and fit in half a word; double may be 64 bit, and take up a whole word; but both are addressable and the difference is transparent from the C programmer's perspective.)

---

### Post by 3Miro on 2011-11-30
> **trent.josephsen said:**
> 
The number of addressable memory locations and the size of the largest number the ALU or floating-point coprocessor can handle.

(Most 64 bit machines do indeed have a 64 bit word size.  The significance of that diminishes greatly, however, when the word is not the smallest addressable chunk of memory.  For example, on a 64 bit system, float may be 32 bit, and fit in half a word; double may be 64 bit, and take up a whole word; but both are addressable and the difference is transparent from the C programmer's perspective.)

On 64-bit machines pointers are 64-bit hence you can address more memory. For consistency, float is float and double is double, however, double* is bigger on 64-bit machine.

The second advantage is that the number of registers is larger. Take the following overly simplistic example:
```
int foo1();
void foo2( int* a, int *b);
```
On a 32-bit machine, foo1 will return the int value stored in a register (fastest possible way), while foo2 will write the values to RAM. On the other hand, on a 64-bit machine both cases would return the values in the registers.

I don't think modern day processors have too much trouble working with half-words. Floating point computations are accelerated by special registers so that on a 64-bit machine both floats and doubles are processed faster.

If you want extra precision, there are extended formats that would allow you to use 128 bit floats (some CPUs support floats of size around 90). Look at libquadmath. However, those formats are not widely used yet.

---

### Post by Dirich on 2011-11-30
Thanks [trent.josephsen]("http://ubuntuforums.org/member.php?u=763491") for the explaination. And no need to apologize, it's kind enough that you dedicated some of your time to me to answer my thread. :)

Thanks 3Miro for the libquadmath, I'll check them right now.

---

