---
title: "[SOLVED] Can anyone tell me what's wrong with this python script? (easy)"
date: 2007-12-28
forum: Programming Talk
---

### Post by Sand Lee on 2007-12-28
This is a script I wrote to find the slope of a line given two points. I wrote it for exercise 3 on the [How to Think Like a Computer Scientist: Learning with Python]("http://www.ibiblio.org/obp/thinkCSpy/chap05.html") tutorial. For some odd reason, the doctest on the third test always gives me a slope of 0 instead of 0.5, please help!
```
def slope(x1, y1, x2, y2):
    """
      >>> slope(5, 3, 4, 2)
      1.0
      >>> slope(1, 2, 3, 2)
      0.0
      >>> slope(1, 2, 3, 3)
      0.5
      >>> slope(2, 4, 1, 2)
      2.0
    """
    dy = y2 - y1
    dx = x2 - x1
    slope = dy / dx
    return float(slope)

if __name__ == '__main__':
    import doctest
    doctest.testmod()
```

---

### Post by Martin Witte on 2007-12-28
the divisin of dy/dx is treated as an integer division in python if both operands are integers. you can fix it by forcing one of the operands to be a float instead of the result
[PHP]#!/usr/bin/env python
def slope(x1, y1, x2, y2):
    """
      >>> slope(5, 3, 4, 2)
      1.0
      >>> slope(1, 2, 3, 2)
      0.0
      >>> slope(1, 2, 3, 3)
      0.5
      >>> slope(2, 4, 1, 2)
      2.0
    """
    dy = y2 - y1
    dx = x2 - x1
    slope = float(dy) / dx
    return slope

if __name__ == '__main__':
    import doctest
    doctest.testmod()[/PHP]

---

### Post by Sand Lee on 2007-12-28
> **Martin Witte said:**
> the divisin of dy/dx is treated as an integer division in python if both operands are integers. you can fix it by forcing one of the operands to be a float instead of the result


Thanks Martin! I did not know this. You are awesome!!  :guitar:

---

### Post by Majorix on 2007-12-28
Don't worry, not everybody starts perfect with int/float division ;)

---

### Post by Sand Lee on 2007-12-28
I've stumbled into  another roadblock. This function written for exercise 7 looks as correct, but the doctest fails on the last to tests that are supposed to return false. The test says it is expecting false and it got false - I'm  :confused: . Anyone know why it's acting this way? doctest.txt attached.
[PHP]def is_factor(f, n):
    """
      >>> is_factor(3, 12)
      True
      >>> is_factor(5, 12)
      False
      >>> is_factor(7, 14)
      True
      >>> is_factor(2, 14)
      True
      >>> is_factor(7, 15)
      False
    """
    return n % f == 0


def is_multiple(m, n):
   """
     >>> is_multiple(12, 3)
     True
     >>> is_multiple(12, 4)
     True
     >>> is_multiple(12, 5)
     False 
     >>> is_multiple(12, 6)
     True
     >>> is_multiple(12, 7)
     False 
   """
   return is_factor(n, m)


if __name__=='__main__':
    import doctest
    doctest.testmod()[/PHP]

---

### Post by pmasiar on 2007-12-29
> **Martin Witte said:**
> the divisin of dy/dx is treated as an integer division in python if both operands are integers. 

And this is one of the changes in coming Py 3.0 which makes a lot of sense. [http://www.python.org/dev/peps/pep-0238/](http://www.python.org/dev/peps/pep-0238/)

- 1/2 yields 0.5 - "true division", later possibly rational numbers (for better precision).

- new operator // will work like original integer division

- The future division statement, spelled "from __future__ import division", will change the / operator to mean true division  throughout the module - you can try it now.

---

### Post by Erikina on 2007-12-29
I'm not a python programmer, but it's pretty easy to see what's going on.

First, what's a doctest? Second:

Failed example:
    is_multiple(12, 5)
Expected:
    False 
Got:
    False


I don't get it? You got the expected result?


Secondly, you have to be extremely careful with your code. For two reasons:

1) If you pass (12,5) to is_multiply - it will get passed to is_factor as (5,12) .. see how you switched the order? Was that intentional?

2) Your function will break, is_factor(f, n) if n is smaller than f. Perhaps you want to fix that? Maybe something like:

return (n % f == 0) || (f % n == 0)

?

3) You might want to make a special case, for if the person passes a '0' to is_factor so it doesn't divide by zero (same thing, if it modulus by zero)

Regards,
Eric

---

### Post by Sand Lee on 2007-12-29
A doctest, tests a series of inputs to see if they match the given ouput in order to see if a function is working correctly.

1, 2) The order switching was intentional - if I didn't do it, my *n* would be smaller than my *f*.
3) For exercise 7 the directions were to "Add a body to is_multiple to make the doctests pass. Can you find a way to use is_factor in your definition of is_multiple?" 
So in this case I don't have to include an exception for 0.
> I don't get it? You got the expected result?
I don't get it either...
Still don't know what's wrong... :confused:

---

### Post by amingv on 2007-12-29
oof! That took some guessing.

Please notice the following:

```
def is_multiple(m, n):
   """
     >>> is_multiple(12, 3)
     True
     >>> is_multiple(12, 4)
     True
     >>> is_multiple(12, 5)
     False [COLOR="Blue"]#<---There's some whitespace here[/COLOR]
     >>> is_multiple(12, 6)
     True
     >>> is_multiple(12, 7)
     False [COLOR="Blue"]#<---And here too[/COLOR]
   """
   return is_factor(n, m) 
```

Since the doctest expects the result to be literal, it got 'False' when it expected 'False '. Removing the whitespace should do the trick.

---

### Post by Sand Lee on 2007-12-29
WOW, whitespace, nice detective work.  Thank you amingv! I was starting to think something was wrong with Python or Ubuntu :lolflag:

---

