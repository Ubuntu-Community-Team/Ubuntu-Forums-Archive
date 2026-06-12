---
title: "can't compile math program with cosine algorithm in x64"
date: 2007-12-16
forum: Programming Talk
---

### Post by t.s on 2007-12-16
Hi all,

I've tried to make a simple program with cosine algorithm in openSUSE 10.3. Same result with kubuntu gutsy. Both are 64 bit edition.

> #include <stdio.h>
#include <math.h>

main() {
    printf("Cosine from PI/1 is %f\n", cos(3.1415/1));
}

when I compile that code, it output:
> /tmp/ccCcCz7R.o: In function `main':
cos.c: (.text+0x1c): undefined reference to `cos'
collect2: ld returned 1 exit status

what I know is all the math function now stored in /usr/include/bits/mathcalls.h; but it's said that I cannot use (include) it directly, rather use math.h for that. I've tried both method (include math.h and include mathcalls.h) with same result, FAIL!

Distro bugs or gnu C bug?
Any suggestion?

thanks,
t.s

---

### Post by AlexThomson_NZ on 2007-12-16
try

gcc -lm test.c

---

### Post by AlexThomson_NZ on 2007-12-16
I should probably explain further- including the header file is not enough- you need to actually link against the math library also (-lm = link math)

---

### Post by xtacocorex on 2007-12-16
I know it's  along shot, but if you can't get the cosine function to work, you could always write your own algorithm using a Taylor series expansion.  [http://www.mathreference.com/ca,tfn.html](http://www.mathreference.com/ca,tfn.html)

---

### Post by Majorix on 2007-12-17
> **t.s said:**
> Distro bugs or gnu C bug?

Neither, it's not a bug, you are doing it wrong. You haven't linked in the math library with the -lm option passed to gcc, as stated. That's why as a beginner you should use an IDE, which does all of the compiling etc for you.

---

### Post by maleficent on 2007-12-17
> **Majorix said:**
> Neither, it's not a bug, you are doing it wrong. You haven't linked in the math library with the -lm option passed to gcc, as stated. That's why as a beginner you should use an IDE, which does all of the compiling etc for you.

I think IDEs are a matter of personal preference, beginner or not.

If you decide to persevere with command line compilation though, it might be an idea to RTM: [http://gcc.gnu.org/onlinedocs/](http://gcc.gnu.org/onlinedocs/)  ;)

---

### Post by xtacocorex on 2007-12-17
I don't think I've never had to link using C++ if I've included math.h, but that could be C++.  I take it with C you have to.

But I can agree on learning the command line options; I finally was able to compile a 3D file viewer code Wybiral and I worked (in Linux) in OS X and the only difference was changing 3 lines across 2 files and the options for the compiler.

Learning your tools is a lot more rewarding that using something to do it for you and blindly not understanding why things have to be done.

---

