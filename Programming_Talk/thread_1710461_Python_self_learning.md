---
title: "Python self learning"
date: 2011-03-19
forum: Programming Talk
---

### Post by hdanap on 2011-03-19
Hi guys,

1st thing i want to say, this is not an assignment im readn/learning python on my own.

i came across this problem, i really dont understand it, i know how to  write doctest when it come to numbers but i really don't know what the  book wants me to do, if i could be channeled in the right direction.

Question:

Write Python code to make each of the following doctests pass:
 """
  >>> type(fruit)
  <type 'str'>
  >>> len(fruit)
  8
  >>> fruit[:3]
  'ram'
"""

am i supposed to write a function or just write code in a script?

pls help

my attempt


def word(s):
    """
    >>> type(fruit)
    <type 'str'>
    >>> len(fruit)
    8
    >>> fruit[:3]
    'ram'
    """
    fruit='ramadana'
    if s == fruit:
        x= type(fruit)
        y= len(fruit)
        z= fruit[:3]

---

### Post by cjhabs on 2011-03-19
fruit = "xxxxxram"

Then run each of the commands and you'll get the response shown - i.e. it is an 8 character string ending in "ram"

---

### Post by hdanap on 2011-03-19
when i do :

"""
>>> type(fruit)
<type 'str'>
>>> len(fruit)
8
>>> fruit[:3]
'ram'
"""
fruit= 'adanaram'
print type(fruit)
print len(fruit)
print fruit[:3]

i get  from the interpreter:

<type 'str'>
8
ada
3 items had no tests:
    __main__
    __main__.find
    __main__.without_vowels
0 tests in 3 items.
0 passed and 0 failed.
Test passed.

from this i understand that no test was executed, how do i make the test run???

---

### Post by hdanap on 2011-03-20
i figured it out, this is the code that did the trick


fruit= 'ramadana'

def word(s):
    """
    >>> type(fruit)
    <type 'str'>
    >>> len(fruit)
    8
    >>> fruit[:3]
    'ram'
    """
    #s=str(s)
    #x=type(s)
    #y=len(s)
    #z=s[:3]
    #print type(s)
    #print len(s)
    #print s[:3]


the commented code could be uncommented and the test still works

---

### Post by cjhabs on 2011-03-20
You don't need print:
fruit= 'adanaram'
type(fruit)
len(fruit)
fruit[:3]

---

