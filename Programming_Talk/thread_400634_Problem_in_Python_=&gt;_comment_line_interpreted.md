---
title: "Problem in Python =&gt; comment line interpreted??"
date: 2007-04-03
forum: Programming Talk
---

### Post by gammaknife on 2007-04-03
hi there, I'm just beginning my first steps in programming
I encountered something funny when I ran the program that follows:

---------------------------------------------------------------------------------------------------------
#here is something extremely important. First the statements
def imprimdeux(x):
 print x + x
imprimdeux("x")         


# output va être x x 
# si on fait imprimdeux('zaille' ou "zaille"), l'imput va être zaille zaille 
-----------------------------------------------------------------------------------------------------------

the program works as "intended" (don't know if that thing can be called a program :p) but I receive the following message in my ouput :
 
"sys:1: DeprecationWarning: Non-ASCII character '\xc3' in file funcpam.py on line 16, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details"

I thought comments were not supposed to be interpreted by the computer so I wonder what's going on...

Can someone shed some light on this great mystery...?

---

### Post by dwblas on 2007-04-03
Obviously it checks for UTF encoding before it checks for comments.

---

### Post by gammaknife on 2007-04-03
what's obvious for you isn't obvious for me :)

Care to explain what UTF encoding means?

---

### Post by ssam on 2007-04-03
python expects files to be in ascii, if yours is in UTF then you need to start the file with

```
#!/usr/bin/python
# -*- coding: UTF-8 -*-
```


[http://en.wikipedia.org/wiki/Unicode](http://en.wikipedia.org/wiki/Unicode)
[http://en.wikipedia.org/wiki/Ascii](http://en.wikipedia.org/wiki/Ascii)
[http://www.python.org/dev/peps/pep-0263/](http://www.python.org/dev/peps/pep-0263/)

---

### Post by gammaknife on 2007-04-03
many thanks!

---

### Post by bashologist on 2007-04-03
That may be the problem. But the problem I see is there's no indentation in his example.
```
#!/usr/bin/env python
def imprimdeux(x):
	print x + x
imprimdeux("x")
```
This'll work.

---

### Post by WW on 2007-04-03
The indenting was probably lost when the code was posted to the forum without enclosing it in [ code ] and [ /code ].

---

### Post by gpolo on 2007-04-03
Just to clarify, the comments are ignored but if any of them got characters that are not in ascii charset, you need to set an encoding at beginning of your .py

---

### Post by pmasiar on 2007-04-03
BTW when I run OP code in IDLE, it suggested correct fix: # -*- coding: UTF-8 -*-

It really helps to use good tools and do not fight them :-)

---

