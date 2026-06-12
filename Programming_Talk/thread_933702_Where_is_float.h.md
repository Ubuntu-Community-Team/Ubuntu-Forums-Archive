---
title: "Where is float.h?"
date: 2008-09-29
forum: Programming Talk
---

### Post by baruch60610 on 2008-09-29
I was returning to C after a long absence.  To get reacquainted, I started out with a simple program using the sqrt function.  To my best recollection, the header file for that would have been float.h.  However, to my horror I discovered there *is* no such file anywhere I can find.  Moreover, there appears not to be any such file on gnu.org or anywhere else I can get the GNU C library.

What happened?  I'm aware of the changes to C++ that have files such as cfloat and cmath, and I can get my program going in C++.  But how do you write programs with floating point calculations in C?  Where's float.h, I wonder?

I'd appreciate any help I can get.  I've tried Googling for this, tried checking "how-to" sites, searched on gnu.org and ubuntu.com, all to no avail.

---

### Post by Sinkingships7 on 2008-09-29
I believe you're looking for math.h. For floating point calculations, couldn't you just use the 'double' type?

---

### Post by baruch60610 on 2008-09-29
Hi, thanks for your suggestion.

I'm familiar with math.h, and I tried that.  It didn't work.  Really, I'm not concerned with float vs. double; I'm just trying to find out where the sqrt function is defined.  I don't find it anywhere, and when I try to compile using math.h, I get an error (undefined reference to sqrt).

When I Googled this, various sources confirmed my recollection that float.h contains the declaration for this function.  However, float.h doesn't exist on my system.  I downloaded the GNU C library and unpacked it, just to make sure I didn't somehow delete that file, but it's not *in* their library.

I tried the ieee754.h file, math.h, and various others I thought might have it.  I tried grepping the files for a definition of sqrt (no such luck).  I haven't got a clue.

Like I said, I've got no such problem with C++, but I'm getting really frustrated with C.

---

### Post by bruce89 on 2008-09-29
> **baruch60610 said:**
> Hi, thanks for your suggestion.

I'm familiar with math.h, and I tried that.  It didn't work.  Really, I'm not concerned with float vs. double; I'm just trying to find out where the sqrt function is defined.  I don't find it anywhere, and when I try to compile using math.h, I get an error (undefined reference to sqrt).


You have to link to libm (-lm).

---

### Post by dwhitney67 on 2008-09-29
Sinkingships7 advice is correct.

[PHP]#include <math.h>
#include <stdio.h>

int main()
{
  double sixteen = 16.0;
  double four    = sqrt( sixteen );

  printf( "four = %f\n", four );

  return 0;
}[/PHP]
To compile:
```
gcc sqrt_test.c -lm -o sqrt_test
```

If you are compiling in C++, you do not require the -lm; and use g++ instead.

P.S.  For more details concerning sqrt(), pow(), or any other C-library function, refer to the man-pages.

---

### Post by baruch60610 on 2008-09-29
A big thank you to Sinkingships7, bruce89, and dwhitney67.  I hadn't known about the library, but when I added that option to gcc, it compiled and linked properly.

I had tried the man pages, but could find no information about any of those functions.  I'm not sure if I'm missing something, or whether I was trying the wrong options for man (I tried man sqrt, man libc, man glibc, and various other possibilities).

But thanks to everyone for your help.

---

### Post by dwhitney67 on 2008-09-29
> **baruch60610 said:**
> A big thank you to Sinkingships7, bruce89, and dwhitney67.  I hadn't known about the library, but when I added that option to gcc, it compiled and linked properly.

I had tried the man pages, but could find no information about any of those functions.  I'm not sure if I'm missing something, or whether I was trying the wrong options for man (I tried man sqrt, man libc, man glibc, and various other possibilities).

But thanks to everyone for your help.
To get the man-pages:
```
sudo apt-get install manpages-dev
```

---

### Post by baruch60610 on 2008-10-01
dwhitney67, thanks again for this useful information.  Had I known about it sooner, it could have saved me much tearing of hair and gnashing of teeth.

These man pages are going to make my life ever so much easier.  Great!

---

