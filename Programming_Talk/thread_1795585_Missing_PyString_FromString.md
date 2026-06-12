---
title: "Missing PyString_FromString"
date: 2011-07-02
forum: Programming Talk
---

### Post by skytreader on 2011-07-02
I tried to install Pygame via sudo apt-get install python-pygame but since Python 2.6.5 is the default Python that came with Ubuntu, I can't use Pygame on Python 3. So, I copy-pasted the Pygame (and NumPy, as I heard somewhere that Pygame uses it too) folder from **/usr/lib/python2.6/dist-packages/** to **/usr/lib/python3/dist-packages/** . However, importing Pygame in Python 3 gives the following error message:

```
Python 3.1.2 (r312:79147, Sep 27 2010, 09:45:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python3.1/dist-packages/pygame/__init__.py", line 95, in <module>
    from pygame.base import *
ImportError: /usr/lib/python3.1/dist-packages/pygame/base.so: undefined symbol: PyString_FromString
>>> 

```

What did I miss? How do I import/install Pygame successfully in Python 3?

---

### Post by NovaAesa on 2011-07-02
According to the FAQs on the PyGame website, pygame hasn't yet been fully ported to Python 3, but there is partial support for some things. You probably want to work out if enough modules have been ported yet before deciding if you want to use pygame with Python 2 or Python 3. [http://pygame.org/wiki/FrequentlyAskedQuestions#Does Pygame work with Python 3?](http://pygame.org/wiki/FrequentlyAskedQuestions#Does Pygame work with Python 3?)

---

