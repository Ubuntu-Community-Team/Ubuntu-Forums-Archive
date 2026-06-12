---
title: "A little Python question"
date: 2010-01-04
forum: Programming Talk
---

### Post by C++buntu on 2010-01-04
Hi everyone,

I'm puzzled, I'm new to programming but I work my way up with Python. I have a question for the guru's out there.

There's my code:

```

# Filename: convert_temp.py
def C2F(C):
    """ C2F(C) convert a Celsius to a Fahrenheit temperature.

        Input:       C:  Celsius degree.
        Output:     F:  Fahrenheit degree.

        Example:    >>> C2F(0)
                          32.0
    """
    if C < -273.15:
        raise ValueError('C = %g is a non-physical value.' % C)
    else:
        value = (9./5)*C + 32
    return value

```Now, when I run this in IPython, I obtain the following:

```

In [1]: from convert_temp import *

In [2]: C2F(0)
Out[2]: 32.0

In [3]: C2F(-400)
ERROR: An unexpected error occurred while tokenizing input
The following traceback may be corrupted or invalid
The error message is: ('EOF in multi-line statement', (38, 0))

---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

/home/steeve/Py4cs/problems/chapter 03/<ipython console> in <module>()

/home/steeve/Py4cs/problems/chapter 03/convert_temp.pyc in C2F(C)
     16     """
     17     if C < -273.15:
---> 18         raise ValueError('C = %g is a non-physical value.' % C)
     19     else:
     20         value = (9./5)*C + 32

ValueError: C = -400 is a non-physical value.

```Any help for my error?

Thanks,

C++buntu

---

### Post by diesch on 2010-01-04
Works for me:
```

In [1]: from convert_temp import *

In [2]: C2F(0)
Out[2]: 32.0

In [3]: C2F(-400)
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

/home/diesch/<ipython console> in <module>()

/home/diesch/convert_temp.py in C2F(C)
     10     """
     11     if C < -273.15:
---> 12         raise ValueError('C = %g is a non-physical value.' % C)
     13     else:
     14         value = (9./5)*C + 32

ValueError: C = -400 is a non-physical value.


```

The line numbers suggest that the file you are using contains not only the code you've given. I guess that the problem is caused by this extra lines.

---

### Post by Axos on 2010-01-04
I plead ignorance about IPython but I ran your program using ordinary python and it seemed to work fine (I used the file name "c2f.py", thus the "import c2f"):

Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import c2f
>>> c2f.C2F(0)
32.0
>>> c2f.C2F(-400)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "c2f.py", line 12, in C2F
    raise ValueError('C = %g is a non-physical value.' % C)
ValueError: C = -400 is a non-physical value.

---

### Post by C++buntu on 2010-01-04
Thanks for the reply, I will comment my other lines of code in the file to check where the error comes from.

Cheers, 

Danke

---

### Post by nvteighen on 2010-01-05
Hm... My guess is that you've got a tab/space mix... or that you edited the code in Windows or Mac.

---

