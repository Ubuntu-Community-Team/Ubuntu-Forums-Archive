---
title: "Peculiar GCC Behaviour"
date: 2007-10-20
forum: Programming Talk
---

### Post by ankursethi on 2007-10-20
I've #included <math.h> in my program.

This works :
```
pow(2, 2) ;
```

But this does not :
```
int q = 2 ;
pow(2, q) ;
```

I get an error saying "undefined reference to pow())". I compiled the same code with g++ to make the damn thing work.

What's going on here?

---

### Post by Lux Perpetua on 2007-10-20
You have to compile with the switch "-lm" so that it links the math library. For your first code example, I bet GCC is just trying to be smart and thinks that if you have "pow(2,2)" in your code, you probably just mean "4."

---

### Post by dwhitney67 on 2007-10-20
Also, gcc is for C programs, g++ for C++.  Lastly, pow() arguments should be declared as doubles, not ints.  Reference the man-page for pow() so that you will learn:

1) include <math.h>
2) double pow( double x, double y );
3) link with -lm

P.S.  The -lm tells the gcc compile to link in /usr/lib/libm.a with your program, thus resolving the implementation of pow().  The definition of pow() comes from /usr/include/math.h.

---

### Post by ankursethi on 2007-10-21
I know the difference between GCC and G++. I just tried G++ because it can compile C code as well. I just wanted to check whether there was a syntax error.

Anyway, since when do we have to link any program using math.h with libm.a? I can remember using math.h on Ubuntu without having to link with libm. Something new, or is my memory failing me?

Anyway, thanks :) It works now.

---

### Post by dwhitney67 on 2007-10-21
> **ankursethi said:**
> I know the difference between GCC and G++. I just tried G++ because it can compile C code as well. I just wanted to check whether there was a syntax error.

Anyway, since when do we have to link any program using math.h with libm.a? I can remember using math.h on Ubuntu without having to link with libm. Something new, or is my memory failing me?

Anyway, thanks :) It works now.
You're welcome.

As for the usage of libm.a, as far as I know, you do not need it for pow().  However, that may change "tomorrow".  For other math functions, such as cos(), sin(), tan(), etc., the math library is required.  Anyhow, it is always best to follow the instructions as provided in the man-pages.

---

### Post by hilltop_yodeler on 2008-03-14
I have two questions:

FIRST: I am trying to learn more about using the pow() function, but I can't seem to view the man page in Ubuntu.  I am using the command:
> man 3 pow
This seems to work on Fedora, but I can't seem to pull up the man page in Ubuntu.  GCC works great for me, but is there some other library that I need to download in order to view the man pages?  I have installed gcc-doc in addition to gcc.  The error I get after typing in the command listed above is:
No manual entry for pow in section 3
How can I access the man page for pow()?

SECOND: dwhitney67, you said to always define your pow() function as a double.  What if I am simply trying to print out a power of two numbers.  For example:

```

printf("%lf\n", pow(2,7));  // I used %lf for the double value

```

I realize that I could declare a double variable and set it equal to the value of pow(2, 7), and then print the double variable, but what if I wanted to directly use the pow() function within my printf statement?

Thanks!

---

### Post by hod139 on 2008-03-14
You need to install manpages-dev for the development manpages.  As for printing pow,  if this is C code, pow is only defined for type double and the code snippet you pasted shows how to print the return value, so I'm confused what you are asking.

---

### Post by WW on 2008-03-14
> **hilltop_yodeler said:**
> I have two questions:

FIRST: I am trying to learn more about using the pow() function, but I can't seem to view the man page in Ubuntu.  I am using the command:
> man 3 pow

Install the package **manpages-dev**.

> **hilltop_yodeler said:**
> 
SECOND: dwhitney67, you said to always define your pow() function as a double. [...]

The pow function takes two double arguments. (Once you get the manpage installed, you'll see :)  You don't have a choice here, unless you rewrite your own.  If you use integer arguments, the compiler will implicitly convert them to double.

---

### Post by KaeseEs on 2008-03-14
A quick note on development manpages, in addition to **manpages-dev** you get a few more manpages by also installing **glibc-doc** (primarily pthread stuff).

---

### Post by hilltop_yodeler on 2008-03-14
Great!  Thanks hod139  and WW.  The man pages are working fine now.  And, for some reason, the code that I had posted earlier was not working correctly for me at the time, but it is now.  

I have been asked to write a function that will convert a decimal integer to binary, and one of the requirements is that it must use the pow() function, so I am trying to gain a better grasp of how pow() works.  This will be fun to figure out.  Thank you both for your help!

---

