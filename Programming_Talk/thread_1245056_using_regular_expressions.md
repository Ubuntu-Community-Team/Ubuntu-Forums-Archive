---
title: "using regular expressions"
date: 2009-08-20
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-08-20
I am trying to understand the regular expressions module, and am having some difficulties. Can someone please help.

```

>>> a='12*34+56/78'
>>> re.split('[+-*/]',a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/re.py", line 167, in split
    return _compile(pattern, 0).split(string, maxsplit)
  File "/usr/lib/python2.6/re.py", line 245, in _compile
    raise error, v # invalid expression
sre_constants.error: bad character range
>>> re.split('\W',a)
['12', '34', '56', '78']

```

Can someone please explain why the first condition doesn't seem to work.

Another snippet which i don't seem to understand, is the following,
```

>>> a='1+++++2+3+4'
>>> re.split('\+{1}',a)
['1', '', '', '', '', '2', '3', '4']

```
This is what i expected, ['1+++++2','3','4']. Can someone explain the fallacy, and what should be the re for getting this kind of output.

---

### Post by Arndt on 2009-08-20
> **i.mehrzad said:**
> I am trying to understand the regular expressions module, and am having some difficulties. Can someone please help.

```

>>> a='12*34+56/78'
>>> re.split('[+-*/]',a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/re.py", line 167, in split
    return _compile(pattern, 0).split(string, maxsplit)
  File "/usr/lib/python2.6/re.py", line 245, in _compile
    raise error, v # invalid expression
sre_constants.error: bad character range
>>> re.split('\W',a)
['12', '34', '56', '78']

```

Can someone please explain why the first condition doesn't seem to work.

Another snippet which i don't seem to understand, is the following,
```

>>> a='1+++++2+3+4'
>>> re.split('\+{1}',a)
['1', '', '', '', '', '2', '3', '4']

```
This is what i expected, ['1+++++2','3','4']. Can someone explain the fallacy, and what should be the re for getting this kind of output.

In the first problem, you have the character collection +-*/, but the way you write it, it's interpreted as a range, since there is a hyphen in the middle. Put the hyphen as the first character instead:

```
re.split('[-+*/]',a)
```

You can quote the hyphen with \ instead, but I'm not sure that works in all RE implementations.

As for the second problem, I see what happens but I don't know the solution in python. You want some way to express that '+' is a splitting part, but '++' isn't.

---

### Post by unutbu on 2009-08-20
```
#!/usr/bin/env python
import re
a='1+++++2+3+4'
b=re.split('\+(?=[^+])',a)
print(b)
```

Returns
```

['1++++', '2', '3', '4']
```

Here is a breakdown of the regex '\+(?=[^+])': 
'\+' means look for a plus-sign
'(?=...)' means look-ahead for the ... pattern, but don't consume the string
'(?=[^+])' means look-ahead for [^+]
'[^+]' means match any character other than a plus-sign


Note that ['1++++', '2', '3', '4'] lacks one of the plus-signs you were expecting.
That is because re.split removes the plus-sign that matches. 

I do not know how to make a regex that produces the exact output you expected.

---

### Post by smartbei on 2009-08-21
Why not use groups to match what you want, instead of split to match what you don't? To match all character groups:
```

re.findall("(\d+)", "123+45-2+1")

```
The second problem you had is also solvable using groups (you can use the pipe operator to choose between two different regexes depending on circumstances), but it doesn't look very useful...

---

