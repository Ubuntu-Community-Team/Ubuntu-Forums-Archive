---
title: "Question about Python"
date: 2011-04-30
forum: Programming Talk
---

### Post by samh785 on 2011-04-30
I'm attempting to teach myself to program in Python. One of the practice assignments that I found asked me to create a function that will output a user defined number of [Fibonacci numbers]("http://en.wikipedia.org/wiki/Fibonacci_number"). After becoming desperate, I turned to an example I found online. After toying around with it for a while, I noticed that the difference between my code and the example I found online was this:

(functional)
```


    def function(var1):
        var2 = 0
        var3 = 1
        for var4 in range(0, var1):
            print var2
            var2,var3 = var3, var2 + var3


```v.s. mine: (nonfunctional)

```


def function(var1):
        var2 = 0
        var3 = 1
        for var4 in range(0, var1):
            print var2
            var2 = var3
            var3 = var2 + var3  


```I just want to understand how my code is different from the example I found online.

EDIT: To clarify, my code doesn't work, while the other version is fully functional.

---

### Post by Gerontion on 2011-04-30
It looks like, in your version, you're doubling var3 (by setting var2 equal to var3 and then adding var3 to that new value). I'm not sure quite how the assignment works in Python (I'm actually sitting here with a copy of 'How to Think Like a Computer Scientist: Learning with Python' right at this moment!) but I guess in the online version, by keeping everything in the same assignment, it's using the old value of var2 to generate the new var3.

---

A couple of hours later. I've just got to a bit of 'How to Think Like a Computer Scientist' which seems relevant. 

"It is often useful to swap the values of two variables. With conventional assignments,
you have to use a temporary variable. For example, to swap a and b:
>>> temp = a
>>> a = b
>>> b = temp
This solution is cumbersome; tuple assignment is more elegant:
>>> a, b = b, a
The left side is a tuple of variables; the right side is a tuple of expressions. Each
value is assigned to its respective variable. All the expressions on the right side are
evaluated before any of the assignments."

---

### Post by P1C0 on 2011-04-30
This is from Python tutorial:
```
>>> def fib(n):    # write Fibonacci series up to n
...     """Print a Fibonacci series up to n."""
...     a, b = 0, 1
...     while a < n:
...         print a,
...         a, b = b, a+b
...
>>> # Now call the function we just defined:
... fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

So I'd start from [here]("http://docs.python.org/tutorial/index.html") :)

---

### Post by koenn on 2011-04-30
> **Gerontion said:**
>  but I guess in the online version, by keeping everything in the same assignment, it's using the old value of var2 to generate the new var3.


yes, that's it.
in the OP's code, the value of v2 is modified, and then the _new_ value is used to calculate the next value of v3.

A traditional approach would be the use of an additional var to temprarily store the value of v2 before it's changed, and use that :

```

>>> for v1 in range(0, 10) :
...     print v2
...     vtemp = v2
...     v2 = v3
...     v3 = v3 + vtemp


```

---

