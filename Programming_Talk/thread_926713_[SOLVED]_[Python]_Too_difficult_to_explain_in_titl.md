---
title: "[SOLVED] [Python] Too difficult to explain in title"
date: 2008-09-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-22
So I got this string:
> 0xFFFFFF
And how can I use it like a html color?
What is the variable type of 0xFFFFFF?

I tried to convert it to int but didn't work.

I want to use that string as a color to fill the screen.

---

### Post by loell on 2008-09-22
how about..

```
int(0xFFFFFF)
```

---

### Post by CptPicard on 2008-09-22
It's a hexadecimal three-byte int, of value

```

>>> 0xFFFFFF
16777215

```

(as RGB color, that would be  black)

I am not sure what exactly the problem is...

---

### Post by crazyfuturamanoob on 2008-09-22
It is white as rgbcolor. I want to convert string "0xFFFFFF" to int. How?
int(0xFFFFFF) gives me an error

Here is the error:
```

>>> test = int(test)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: '0xFFFFFF'
>>> 

```
test was a string containing "0xFFFFFF"

---

### Post by CptPicard on 2008-09-22
> **crazyfuturamanoob said:**
> It is white as rgbcolor.

Whoops, yes, you're right.

> 
 I want to convert string "0xFFFFFF" to int. How?


Well, I am currently googling here for you on something like "python parsing hexadecimal string to int".. see if you get there first ;)

> int(0xFFFFFF) gives me an error.

It shouldn't... 0xFFFFFF is a literal representation of a number in hex, and it turns automatically to an int, so int(...) is an unnecessary step (at least here it works fine, but it's about has pointless as saying int(5)).

---

### Post by crazyfuturamanoob on 2008-09-22
Solved! It goes like this:
```

test = "0xFFFFFF"
test = int(test, 16)

```

---

### Post by crazyfuturamanoob on 2008-09-22
Found it out with int.__doc__:
```
>>> print int.__doc__
int(x[, base]) -> integer

Convert a string or number to an integer, if possible.  A floating point
argument will be truncated towards zero (this does not include a string
representation of a floating point number!)  When converting a string, use
the optional base.  It is an error to supply a base when converting a
non-string. If the argument is outside the integer range a long object
will be returned instead.
>>> 

```

---

### Post by ghostdog74 on 2008-09-22
Python has made it easy such that we forgot how to do the basic stuffs. 
Eg FFFE = ( decimal value of "E" * 16 ^ 0) + (decimal value of "F" * 16 ^ 1 )  + ( ...and so on ).
You can easily create such a function yourself.

---

