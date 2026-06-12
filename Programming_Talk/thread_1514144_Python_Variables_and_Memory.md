---
title: "Python Variables and Memory?"
date: 2010-06-20
forum: Programming Talk
---

### Post by McRat on 2010-06-20
```

import time

def arccot(x, unity):
     sum = xpower = unity // x
     n = 3
     sign = -1
     while 1:
         xpower = xpower // (x*x)
         term = xpower // n
         if not term:
             break
         sum += sign * term
         sign = -sign
         n += 2
     return sum
 
def pi(digits):
     unity = 10**(digits + 10)
     pi = 4 * (4*arccot(5, unity) - arccot(239, unity))
     return pi // 10**10

places = 1

while places:

     places = int(input ("how many places? "))
     t = time.time()
     print ("The answer is", pi(places))
     print ("time.time()",time.time()-t)
```

This is a Pi calculator I found on a public website, and I was playing with it.  

I do not understand how Python can return a number with 200,000 digit mantissa (resolution).

Is it a string?  If so, how do you know when a Float, or Integer is a string?

Also when you execute it, Python will lag badly after execution is complete.  What is going on in the background that would make it lag?  Is there a way to "free it up" without shutting down?

---

### Post by Bachstelze on 2010-06-20
It is not a string. Python allows for arbitary precision numbers (as available memory allows, of course). Types in Python do not have a fixed size as they do in C. Also what do you mean by "lag badly"? I don't have any lag here as far as I can tell.

---

### Post by McRat on 2010-06-20
Thanks!  That's pretty cool.  I have never seen a programming language that didn't have fixed precision.

Hmmm...

I ran it on 3 machines, OS X, Ub32, Vista 64.  All with 2gb or more RAM.  Somewhere between 200k and 300k all three machines will have a hard time responding to keyboard input when the Python window is in focus.  Other tasks will work fine, just not the Python.  I have to shut down to retest.

---

### Post by Bachstelze on 2010-06-20
> **McRat said:**
> Thanks!  That's pretty cool.  I have never seen a programming language that didn't have fixed precision.


By the way, I should have been more precise, this is only for ints (if you look at your script, it does return an int, not a flot). floats do have fixed precision:

```
Python 3.1.2 (r312:79147, Apr 15 2010, 15:35:48) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1.2345678901234567890
1.2345678901234567

```

There is a third-party module called bigfloat that provides arbitrary precision floats if you want.

By the way, on an unrelated note, when you have a file like that where you define some functions, it's a good idea to do this:

```
import time

def arccot(x, unity):
     sum = xpower = unity // x
     n = 3
     sign = -1
     while 1:
         xpower = xpower // (x*x)
         term = xpower // n
         if not term:
             break
         sum += sign * term
         sign = -sign
         n += 2
     return sum
 
def pi(digits):
     unity = 10**(digits + 10)
     pi = 4 * (4*arccot(5, unity) - arccot(239, unity))
     return pi // 10**10

if __name__ == '__main__':

    places = 1

    while places:
        places = int(input ("how many places? "))
        t = time.time()
        print ("The answer is", pi(places))
        print ("time.time()",time.time()-t)
```

The code after [font=monospace]if __name__ == '__main__':[/font] wil execute only if the file is executed directly, as opposed to imported from another file or an interactive shell session. It is a good idea because it allows you to test the functions individually (otherwise you can only run them as the program tells you to).

---

### Post by Bachstelze on 2010-06-20
> **McRat said:**
> 
I ran it on 3 machines, OS X, Ub32, Vista 64.  All with 2gb or more RAM.  Somewhere between 200k and 300k all three machines will have a hard time responding to keyboard input when the Python window is in focus.  Other tasks will work fine, just not the Python.  I have to shut down to retest.

Are you still using idle? When I run it in a shell, even with 500000 digits, it is still as responsive as it was before, with no residual memory or CPU usage shown in top.

---

### Post by McRat on 2010-06-20
> **Bachstelze said:**
> Are you still using idle? When I run it in a shell, even with 500000 digits, it is still as responsive as it was before, with no residual memory or CPU usage shown in top.

Thanks for the tips!  All I did was copy the two functions, and dressed to make a "speed test".

Yes, I ran from IDLE.  I just ran it directly from V64, and it doesn't lag at 200000 (took 103 seconds).

I'll try the other two.  I'm just playing around, so I'm very grateful for any tips, hints or tricks.

That formula is from the year 1706.  It's hard to believe how smart those mathematicians were back then, with no pencils, erasers, slide-rules, or calculators.  Very humbling.

---

### Post by nvteighen on 2010-06-21
The "lag" may be related to Python's garbage collector.

BTW, I don't see any definition for 'xpower' in arccot(). Was it 'x' (the one in the argument list)?

---

### Post by McRat on 2010-06-21
> **nvteighen said:**
> The "lag" may be related to Python's garbage collector.

BTW, I don't see any definition for 'xpower' in arccot(). Was it 'x' (the one in the argument list)?

One of the first lines, sum = xpower = unity / x

---

### Post by mbsullivan on 2010-06-21
I like that Python supports multi-precision arithmetic out of the box. I
kinda wish it did it (1) faster and (2) with support for multi-precision floats, though.

> Thanks! That's pretty cool. I have never seen a programming language that didn't have fixed precision.

Under C/C++, it's fast and possible through libraries. The most popular (I think) are [GMP]("http://gmplib.org/")/[MPFR]("http://www.mpfr.org/"), which support (1) big ints (2) exact computation of rational numbers (3) arbitrary precision FP.

I've found the [MPFR C++ bindings]("http://www.holoborodko.com/pavel/?page_id=12") to be solid, if you're using C++.

It's possible to get (1) faster arbitrary precision arithmetic and (2) support for rationals and floats under Python by using [mpmath]("http://code.google.com/p/mpmath/")/[gmppy]("http://code.google.com/p/gmpy/"). You lose a bit of transparency, though.

Mike

---

### Post by soltanis on 2010-06-21
> **McRat said:**
> Thanks!  That's pretty cool.  I have never seen a programming language that didn't have fixed precision.

A lot of programming languages have this feature. It seems to be common among functional languages, e.g. ANSI Common Lisp and Haskell, probably because those languages are intended for things such as mathematical problem solving and simulations.

GnuMP is a library which supports calculations with arbitrary precision numbers in C, but of course, they are implemented as library functions and not built-in language operations.

---

### Post by nvteighen on 2010-06-22
> **McRat said:**
> One of the first lines, sum = xpower = unity / x

Oh, I didn't know you could do that :P It's nice to learn something new when you've thought you already learned it all ;)

---

