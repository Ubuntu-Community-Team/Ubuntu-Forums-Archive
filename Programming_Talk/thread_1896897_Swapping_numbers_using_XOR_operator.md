---
title: "Swapping numbers using XOR operator"
date: 2011-12-18
forum: Programming Talk
---

### Post by achuth on 2011-12-18
Sir,
For swapping two numbers, say x and y, the following single statement will help in C.
**[FONT="Courier New"]x^=y^=x^=y;[/FONT]**

But when I implemented this in a shell script, it is not working.
I used the following code in my shell script
**[FONT="Courier New"]$((x^=y^=x^=y))[/FONT]**

When I echoed the variables to the screen, one number gets the swapped value but the other always gets assigned a value 0.

Please give me a working version of the above single statement in a shell script.

---

### Post by Vaphell on 2011-12-18
when you split this expression to pieces it works fine.

```
$ x=15; y=403
$ (( x^=y, y^=x, x^=y ))
$ echo x=$x y=$y
x=403 y=15

```

---

### Post by Arndt on 2011-12-18
> **achuth said:**
> Sir,
For swapping two numbers, say x and y, the following single statement will help in C.
**[FONT="Courier New"]x^=y^=x^=y;[/FONT]**

But when I implemented this in a shell script, it is not working.
I used the following code in my shell script
**[FONT="Courier New"]$((x^=y^=x^=y))[/FONT]**

When I echoed the variables to the screen, one number gets the swapped value but the other always gets assigned a value 0.

Please give me a working version of the above single statement in a shell script.

What you are doing in C is actually not well-defined, even though it happens to give the result you expect with your compiler. With warnings turned on, gcc reports this:

```
$ gcc -Wall -c xorr.c
xorr.c: In function ‘main’:
xorr.c:12: warning: operation on ‘x’ may be undefined
```

Where did you see this expression?

---

### Post by Vaphell on 2011-12-18
yup
[http://en.wikipedia.org/wiki/XOR_swap_algorithm](http://en.wikipedia.org/wiki/XOR_swap_algorithm)

> Code example

A C function that implements the XOR swap algorithm:

```
 void xorSwap (int *x, int *y) {
     if (x != y) {
         *x ^= *y;
         *y ^= *x;
         *x ^= *y;
     }
 }
```

Note that the code does not swap the integers passed immediately, but first checks if their addresses are distinct. This is because, if the addresses are equal, the algorithm will fold to a triple *x ^= *x resulting in zero.

**The body of this function is sometimes seen incorrectly shortened to if (x != y) *x^=*y^=*x^=*y;. This code has undefined behavior, since it modifies the lvalue *x twice without an intervening sequence point.**

---

### Post by achuth on 2011-12-18
What you mean by "**intervening sequence point**"?. Care to explain?

---

### Post by MadCow108 on 2011-12-18
> A sequence point in imperative programming defines any point in a computer program's execution at which it is guaranteed that all side effects of previous evaluations will have been performed, and no side effects from subsequent evaluations have yet been performed

[http://en.wikipedia.org/wiki/Sequence_point](http://en.wikipedia.org/wiki/Sequence_point)

it boils down to:
the compiler is allowed to execute that expression in any order it wishes too and that may produce a result you did not intend.
the more classical example of this:
```
i = i++;
```
which value i has in the end is undefined. due to the lack of sequence points

---

