---
title: "Python not doing what I expect, no response. Help me, I`m new to Python"
date: 2013-09-13
forum: Programming Talk
---

### Post by matehussilvapb on 2013-09-13
I wrote a program to solve square root with the newton`s algorithm (square root of x, take a guess, keep doing g + x/g until it`s good enough. It is like this:

x = input("i want the sqrrt of:")
def average (a, b):
    av = (a+b)/2.0
    return av

def improve (g, x):
    i = average (g, x/g)
    return i

def ge (g, x):
    d = abs((g*g)-x)
    return (d == 0)

def sqrroot (g, x):
    while (not ge (g, x)):
        improve (g, x)
    return g

def sqrt (x):
    a = sqrroot (1, x)
    return a

print sqrt (x)

When I try to run it on terminal it does nothing ! it takes the first input and i need to open another terminal because it came useless, cant do nothing and it doesnt give me response.
this program is working right if i do it direct on a python terminal, but i wanted to save it and run later

---

### Post by Erik1984 on 2013-09-13
The problem must be this while loop:

```
while (not ge (g, x)):
        improve (g, x)
    return g
```

I know next to nothing about math :P but it can only hang if the while condition is always true. A possible problem could be rounding in the improve() function, so it never actually improves. If you put floats in there they might get converted back to integers.

To debug you could let each function print input and output.

---

### Post by matehussilvapb on 2013-09-13
I did what you said. Tried every function in separate, and when I saw the improve inside the while loop, I realized it kept improving the same numbers on a infinite loop ... So I put g = improve (g, x) , and the guess keeps improving all the way. Thanks man ! I'll post the program here shortly ...

---

### Post by matehussilvapb on 2013-09-13
Here`s the program, it`s working correctly now.
If you want to test it out, and maybe improve it, I`m great.

---

### Post by matehussilvapb on 2013-09-13
> **Euroman said:**
> The problem must be this while loop:

```
while (not ge (g, x)):
        improve (g, x)
    return g
```

I know next to nothing about math :P but it can only hang if the while condition is always true. A possible problem could be rounding in the improve() function, so it never actually improves. If you put floats in there they might get converted back to integers.

To debug you could let each function print input and output.
Solved !

---

### Post by StephenF on 2013-09-14
As Euroman pointed out, the code might hang due to limitations of the available numerical precision and rounding behaviours of the system as a whole. It may run perfectly on your machine for all possible floating point values and then again it might not.

```

import sys

bound = sys.float_info.epsilon  # Value representing the largest rounding error.

def ge (g, x):
    return -bound <= g * g - x <= bound

```

---

### Post by matehussilvapb on 2013-09-14
> **StephenF said:**
> As Euroman pointed out, the code might hang due to limitations of the available numerical precision and rounding behaviours of the system as a whole. It may run perfectly on your machine for all possible floating point values and then again it might not.

```

import sys

bound = sys.float_info.epsilon  # Value representing the largest rounding error.

def ge (g, x):
    return -bound <= g * g - x <= bound

```

actually the code si working great with decimal numbers .... Can you explain this piece of a code ? Thanks

---

### Post by matehussilvapb on 2013-09-14
> **matehussilvapb said:**
> actually the code si working great with decimal numbers .... Can you explain this piece of a code ? Thanks
Now I realized your point, because if you try the sqrt of 2 it creates an infinite loop, so I changed the function ge:
```

def ge
    d = abs(g ** 2 - x)
    return (d < 0.0001)

```
Now it's working great but it can only approximate 3 decimal 'slots'.
and just wondering ... if you can't create a 'loop counter' on python ?

---

### Post by trent.josephsen on 2013-09-15
What's the point of ge, anyway? ge(a,b) is in no way an obvious abbreviation for abs(a**2-b) < precision. It's not clear why you would want to abbreviate that, anyway; the Pythonic approach would be to use it like that.

Similarly, what's the point of improve? All it does is 1/2*(g + x/g); that's a simple expression and calling it "improve" is confusing, since it doesn't have any side effects (improving or otherwise).

What I'm saying here is that you're going a little overboard with the functions. Finding a square root with Newton's method is a four-line algorithm at most. Keep your code simple, and keep the code that does one thing all in one place, and you'll find it much easier to troubleshoot.

So, that said, if the precision isn't good enough, just use a smaller value instead of 0.0001. On my computer, sys.float_info.mant_dig is 53, so I should be able to get 53*lg(10) &#8776; 15 decimal digits of precision just working with Python's floats.

If you increase the precision too much, it'll start failing again; this is just a fact of working with floating-point numbers. If you want better precision than a float can offer, you might consider looking at the decimal.Decimal class, which is part of the Python standard library and supports arbitrary precision arithmetic.

I'm not sure what exactly you mean by "loop counter"; naturally you can always initialize a variable outside a loop and increment it inside the loop if you want to know how many times it executes. Normally, though, there are better ways to do whatever it is you really want to do.

---

### Post by matehussilvapb on 2013-09-17
> **trent.josephsen said:**
> What's the point of ge, anyway? ge(a,b) is in no way an obvious abbreviation for abs(a**2-b) < precision. It's not clear why you would want to abbreviate that, anyway; the Pythonic approach would be to use it like that.

Similarly, what's the point of improve? All it does is 1/2*(g + x/g); that's a simple expression and calling it "improve" is confusing, since it doesn't have any side effects (improving or otherwise).

What I'm saying here is that you're going a little overboard with the functions. Finding a square root with Newton's method is a four-line algorithm at most. Keep your code simple, and keep the code that does one thing all in one place, and you'll find it much easier to troubleshoot.

So, that said, if the precision isn't good enough, just use a smaller value instead of 0.0001. On my computer, sys.float_info.mant_dig is 53, so I should be able to get 53*lg(10) &#8776; 15 decimal digits of precision just working with Python's floats.

If you increase the precision too much, it'll start failing again; this is just a fact of working with floating-point numbers. If you want better precision than a float can offer, you might consider looking at the decimal.Decimal class, which is part of the Python standard library and supports arbitrary precision arithmetic.

I'm not sure what exactly you mean by "loop counter"; naturally you can always initialize a variable outside a loop and increment it inside the loop if you want to know how many times it executes. Normally, though, there are better ways to do whatever it is you really want to do.

Ok, man. I'll try to shorten it up. And that's what I wanted as a loop counter, but I actually realized it some days ago, you can just keep adding to a variable inside the loop.

---

### Post by matehussilvapb on 2013-09-17
Here's the improved version:
```

def sqrt (g, x):
        while ((abs(g*g-x)) > 0.00000000001):
                  g = (g+x/g)/2.0
        return g


```
just put one function inside the other, and make some adjustments.

---

### Post by MG&amp;TL on 2013-09-22
> **matehussilvapb said:**
> Here's the improved version:
```

def sqrt (g, x):
        while ((abs(g*g-x)) > 0.00000000001):
                  g = (g+x/g)/2.0
        return g


```
just put one function inside the other, and make some adjustments.

Much better! However, you have some extraneous brackets around that *abs* call:

```

def sqrt (g, x):
        while abs(g*g-x) > 0.00000000001:
                  g = (g+x/g)/2.0
        return g


``` 

works just fine.

---

### Post by trent.josephsen on 2013-09-22
FWIW, here's the version I wrote:
```
def mysqrt(n, prec=7):
	prec = 0.1**prec
	guess = 1
	while abs(guess*guess - n) > prec:
		guess = (guess + n/guess)/2
	return guess
```

I parameterized the precision so you can determine when you call it how hard it should work. You parameterized the initial guess, which could be better for efficiency in the case where you know the result will be large. Neither approach is decidedly "better", I just thought it might be informative.

---

