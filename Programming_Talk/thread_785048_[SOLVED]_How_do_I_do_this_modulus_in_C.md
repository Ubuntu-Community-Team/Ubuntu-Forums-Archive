---
title: "[SOLVED] How do I do this modulus in C?"
date: 2008-05-07
forum: Programming Talk
---

### Post by anewguy on 2008-05-07
This is a very beginner's question, so bear with me:

I have a file I am reading, and I want to bump a counter each time the number of characters read so far is a multiple of 1024 (actually, it's because constant updating of a label in GTK makes the process slow, so I only want to update the label every 1024 characters).

I have the count defined as a float.  When I have the following in the code I get the error that follows when compiling:

if ((sofar % 1024) == 0)
..
.. sudo code:  update the GUI label
..


 error: invalid operands to binary %

I tried declaring another float and assigning it a value of 1024 and using it in the "if", but I get the same error.  I am EXTREMELY rusty at C, so I vaguely recall things about casting and I suppose that fits in here somewhere.  Since the files could be millions of characters long, I thought I needed a float to hold the value (the file can be a picture or a video, so they can get huge).

Please help an old man who's very rusty at C figure this out.  More than just a "do this", if you could tell me what I am doing wrong and then how to fix it, that would be wonderful!

Thanks in advance! :):)

---

### Post by surhudm on 2008-05-07
What is the type of the variable sofar?

---

### Post by tamoneya on 2008-05-07
when you say you have count defined as a float i assume you mean sofar instead of count.  You just need to cast it to an int.

---

### Post by POW R TOC H on 2008-05-07
It's important to know that variable sofar must be integer :)
Operator % works with integers only...
I realise that you probably already use integers...

---

### Post by anewguy on 2008-05-07
Actually, sofar is the one I declared as a float as I was thinking a video or picture file byte count would be larger than an int or a double.  I'll try the casting thing and see what happens.

Thanks!:)

---

### Post by tamoneya on 2008-05-07
I think you should be alright in terms of file size but if you are worried and want to guaruntee no over flow you could do uint64_t

---

### Post by Lster on 2008-05-07
This may be also useful:

[http://www.cplusplus.com/reference/clibrary/cmath/fmod.html](http://www.cplusplus.com/reference/clibrary/cmath/fmod.html)

---

### Post by samjh on 2008-05-07
> **anewguy said:**
> Actually, sofar is the one I declared as a float as I was thinking a video or picture file byte count would be larger than an int or a double.  I'll try the casting thing and see what happens.

Thanks!:)You don't seem to properly understand the differences between float, int, and double.

A float or double are floating-point numbers.  In simple terms, it means they represent non-integers, such as 1.1 or 0.05.  A double is a more precise variant of float.  Both float and double can represent from 10^-37 to 10^37.  A float has 6 significant digits, a double has 10 significant digits.

An int is for representing integers, ie. whole numbers like 1 or 20.  Minimum for a signed int is -32767, maximum is 32767.  Unsigned int can represent up to 65535 (positive numbers only).  A long int can go from -2147483647 to 2147483647, while an unsigned long int can go up to 4294967295.

The % operator is for int types only.  You cannot use them for float or double types.


PS: The limits I've described may be different depending on your computer system and compiler.

---

### Post by Tuna-Fish on 2008-05-07
> **samjh said:**
> A float or double are floating-point numbers.  In simple terms, it means they represent non-integers, such as 1.1 or 0.05.  A double is a more precise variant of float.  Both float and double can represent from 10^-37 to 10^37.  A float has 6 significant digits, a double has 10 significant digits.

An int is for representing integers, ie. whole numbers like 1 or 20.  Minimum for a signed int is -32767, maximum is 32767.  Unsigned int can represent up to 65535 (positive numbers only).  A long int can go from -2147483647 to 2147483647, while an unsigned long int can go up to 4294967295.

PS: The limits I've described may be different depending on your computer system and compiler.

Where are these numbers from? The eighties?

If he is using a reasonably modern machine with gcc, the sizes for him are, for 32 bit and 64 respectively:
int &#8722;2,147,483,648...+2,147,483,647 / &#8722;2,147,483,648...+2,147,483,647
long &#8722;2,147,483,648...+2,147,483,647 / –9,223,372,036,854,775,808...+9,223,372,036,854,775,807

Also, stating that both float and double have the same range is plain wrong. The IEEE double we all use has 11 bits for exponent, while the 32-bit one has 8. Double has a range of about -10^308...+10^308

---

### Post by WW on 2008-05-07
> **Tuna-Fish said:**
> The IEEE double we all use has 11 bits for exponent, while the 32-bit one has 8. Double has a range of about -10^308...+10^308
Note that this does not mean you could use a **double** to *count* from 0 to 10^308.  For example,

**bigdoubletest.c**
```

#include <stdio.h>

int main(int argc, char *argv[])
    {
    double x,y;
    
    x = 1.0e20;
    y = x + 1;
    if (y == x)
        printf("They are the same!\n");
    return 0;
    }

```

Compile and run:
```

$ gcc -Wall bigdoubletest.c -o bigdoubletest
$ ./bigdoubletest 
They are the same!
$ 

```
(I'm sure Tuna-Fish is well aware of this; I'm pointing it out for those currently learning the subtleties of floating point numbers.)

---

### Post by Lster on 2008-05-07
[QUOTE="samjh (Emphasis mine.)"]A float or double are floating-point numbers. In simple terms, it means they represent non-integers, such as 1.1 or 0.05. A double is a more precise variant of float. Both float and double can represent from 10^-37 to 10^37. **A float has 6 significant digits, a double has 10 significant digits.**[/QUOTE]

[http://en.wikipedia.org/wiki/Single_precision](http://en.wikipedia.org/wiki/Single_precision)
[http://en.wikipedia.org/wiki/Double_precision](http://en.wikipedia.org/wiki/Double_precision)

---

### Post by samjh on 2008-05-07
> **Tuna-Fish said:**
> Where are these numbers from? The eighties?

If he is using a reasonably modern machine with gcc, the sizes for him are, for 32 bit and 64 respectively:
int &#8722;2,147,483,648...+2,147,483,647 / &#8722;2,147,483,648...+2,147,483,647
long &#8722;2,147,483,648...+2,147,483,647 / &#8211;9,223,372,036,854,775,808...+9,223,372,036,854,775,807

Also, stating that both float and double have the same range is plain wrong. The IEEE double we all use has 11 bits for exponent, while the 32-bit one has 8. Double has a range of about -10^308...+10^308

Read the PS.

The values I've described are the minimum specifications from standard C, as defined by float.h and limits.h, **not taking into account implementation differences.**

Sources
float.h: [http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.4.html](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.4.html)
limits.h: [http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.5.html](http://www.acm.uiuc.edu/webmonkeys/book/c_guide/2.5.html)

---

### Post by slavik on 2008-05-07
> **Tuna-Fish said:**
> Where are these numbers from? The eighties?

If he is using a reasonably modern machine with gcc, the sizes for him are, for 32 bit and 64 respectively:
int &#8722;2,147,483,648...+2,147,483,647 / &#8722;2,147,483,648...+2,147,483,647
long &#8722;2,147,483,648...+2,147,483,647 / –9,223,372,036,854,775,808...+9,223,372,036,854,775,807

Also, stating that both float and double have the same range is plain wrong. The IEEE double we all use has 11 bits for exponent, while the 32-bit one has 8. Double has a range of about -10^308...+10^308

actually, MVC++6 has 2 byte int and in gcc int is actually a long int. :)

---

### Post by kaens on 2008-05-07
> **anewguy said:**
> Actually, sofar is the one I declared as a float as I was thinking a video or picture file byte count would be larger than an int or a double.  I'll try the casting thing and see what happens.

Thanks!:)

You may find [this]("http://www.lahey.com/float.htm") an enlightening read. Also [this]("http://www.network-theory.co.uk/docs/pytut/FloatingPointArithmeticIssuesandLimitations.html"), which is python-specific, but is still a decent overview of the issues you deal with with floating point numbers.

---

### Post by samjh on 2008-05-08
> **anewguy said:**
> Actually, sofar is the one I declared as a float as I was thinking a video or picture file byte count would be larger than an int or a double.  I'll try the casting thing and see what happens.

Thanks!:)

From standard C, the best type for this concern would be unsigned long int.  That will allow up to 4294967295 (4 giga-bytes if 1 = 1 byte in your program) or more, depending on the machine.

---

