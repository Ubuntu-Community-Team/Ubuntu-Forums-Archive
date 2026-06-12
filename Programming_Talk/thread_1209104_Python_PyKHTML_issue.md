---
title: "Python: PyKHTML issue"
date: 2009-07-09
forum: Programming Talk
---

### Post by ender0887 on 2009-07-09
I have been trying to do some website interaction and screen scraping in python lately, and I found a site that I want to do so with. However, this site is mostly javascript. I heard that PyKHTML is the best python add on for dealing with javascript, so I gathered all the dependencies and installed it.

But when I run it, even if I run an example script they give you, I get an error. Certainly there can't be an error in the Browser() function of PyKHTML?

> Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pykhtml
>>> pykhtml.Browser()
kbuildsycoca running...
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/pykhtml/__init__.py", line 272, in __init__
    init()
  File "/usr/lib/python2.5/site-packages/pykhtml/__init__.py", line 182, in init
    _acceptCookiesGlobally()
  File "/usr/lib/python2.5/site-packages/pykhtml/__init__.py", line 126, in _acceptCookiesGlobally
    advice.writeEntry("CookieGlobalAdvice", "Accept")
AttributeError: 'str' object has no attribute 'writeEntry'
I would appreciate any input on how to solve this. Thanks!

---

