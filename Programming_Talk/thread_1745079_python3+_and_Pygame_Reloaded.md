---
title: "python3+ and Pygame Reloaded"
date: 2011-04-30
forum: Programming Talk
---

### Post by PunkLV on 2011-04-30
Hello,
I'm having real hard time getting python3 to import pygame or pygame reloaded(which is python3.1 compatible).
```
>>> import pygame2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.2/dist-packages/pygame2/__init__.py", line 20, in <module>
    from pygame2.base import *
ImportError: /usr/local/lib/python3.2/dist-packages/pygame2/base.cpython-32mu.so: undefined symbol: PyCObject_FromVoidPtr
```
The exact same msg for both versions of pygame. 
Googling does not help much, besides, I have a vague clue of what to search for, as both pygame and pygame2 were build successfully from source, python-cairo-dev is installed.

It works fine on python2.6, however this is not a option. I have a programm coded in python3.1.

Any help appriciated.

---

### Post by WolfRage on 2012-01-28
Have you found a solution to this yet?

---

### Post by skytreader on 2012-01-29
I've been trying to do this for ages but no one on the internet seems to be able to answer the conundrum of how to install PyGame for Python3 in Ubuntu. The reason is that Ubuntu distros, AFAIK, have Python2.x installed by default so installing/building PyGame defaults to a build for Python2.x . For all I know, this isn't a problem in Windows.

The closest to a solution I've found is this: [http://ubuntuforums.org/showpost.php?p=10306768&postcount=2](http://ubuntuforums.org/showpost.php?p=10306768&postcount=2) **but** it did not work for me. If this answers your woes, I'm happy for you ;D

(Or, try some of the other tips I gathered. They also didn't work for me though: [http://stackoverflow.com/questions/6539472/installing-pygame-for-python-3-1-2-in-ubuntu](http://stackoverflow.com/questions/6539472/installing-pygame-for-python-3-1-2-in-ubuntu))

If, like me, it doesn't work for you, I can only present two alternatives: (1) just work with Python2.x for the moment. Unless your code is already too big, it should be trivial to convert it back to Python2. (2) Use Windows. I opted for (1), by the way.

(And hey, if anything works for you---maybe something you got on your own or some tweaks in the tips I've gathered so far---will you mind updating here? I'd really like to have PyGame on Python3 **in Ubuntu**. Of all my Python codes, only my PyGame codes are in 2. Thanks!)

---

