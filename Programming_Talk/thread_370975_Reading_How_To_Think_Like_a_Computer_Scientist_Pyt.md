---
title: "Reading How To Think Like a Computer Scientist: Python--help with &quot;Hello World&quot;"
date: 2007-02-26
forum: Programming Talk
---

### Post by billdotson on 2007-02-26
I am reading the how to think like a computer scientist book for python programming and I made a text file called hello.py and it;s contents are print "Hello, World!"  I saved it and then opened up python 2.5 and typed $ python hello.py and I got this error:

>>> $ python hello.py
  File "<stdin>", line 1
    $ python hello.py
    ^
SyntaxError: invalid syntax

Why is this doing this.. the book said all you had to do was type $ python hello.py to get it to work

---

### Post by highneko on 2007-02-26
It probably meant to type "python hello.py". Also "./hello.py" would work. Maybe try this in your normal bash prompt not the python interpreter?

---

### Post by Note360 on 2007-02-26
also you just open up the shell not the python shell.

the $ indicates that you should be in a bash, zsh, fish, or other type of standard shell not the python shell. So what you need to do is open the terminal cd to the directory that the script is in and then type python hello.py

---

### Post by billdotson on 2007-02-26
ok I got it.  Now I am doing the sine of an angle.  Here is what I have done in the python interpreter:

import math
degrees = 50
angle = degrees * 2 * math.pi / 360.0
math.sin(angle)
sine = math.sin(angle)
The variable sine I have set to be the sin(angle) but when I change degrees by doing degrees = 40
the when I type variable sine it doesn't change.  

When I change degrees changes then shouldn't that make angle = 40 * 2 * math.pi / 360.0
and make sine change since sine is math.sin(angle)??

---

### Post by WW on 2007-02-26
A language like python does not work like a spreadsheet.  If you change angle, you have to re-execute the statement "sine = math.sin(angle)" to change the value of sine.
>  $ python
Python 2.3.5 (#2, Oct 16 2006, 19:19:48)
[GCC 3.3.5 (Debian 1:3.3.5-13)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import math
>>> angle = 40
>>> s = math.sin(2*math.pi*angle/360.0)
>>> print s
0.642787609687
>>> angle = 50
>>> print s
0.642787609687
>>> s = math.sin(2*math.pi*angle/360.0)
>>> print s
0.766044443119
>>>


---

