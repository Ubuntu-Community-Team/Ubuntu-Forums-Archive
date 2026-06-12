---
title: "Need help debugging my first python script"
date: 2006-11-29
forum: Programming Talk
---

### Post by mssever on 2006-11-29
This is my first experience with Python, and I must confess that it's been quite frustrating. Python works really differently than any other language I've used, so I've been suffering information overload.

At any rate, I'm getting the following exception: ```
Traceback (most recent call last):
  File "./externalPage.py", line 10, in ?
    class BaseHTMLProcessor(HTMLParser):
TypeError: Error when calling the metaclass bases
    module.__init__() takes at most 2 arguments (3 given)
```I've commented out virtually everything. The error occurs in the remaining class definition. Here's all that's uncommented in my script: ```
#!/usr/bin/env python
"""This module loads a URL and rewrites the links so
that they are suitable for passing through a proxy."""

import cgitb; cgitb.enable()
import cgi
import HTMLParser
import htmlentitydefs

class BaseHTMLProcessor(HTMLParser):
    pass

cgi.test()
```Can anyone tell me what's wrong?

---

### Post by po0f on 2006-11-29
mssever,

Notice that it's a TypeError.  Try:
```
[FONT="Courier New"]import HTMLParser

class BaseHTMLProcessor(HTMLParser.HTMLParser):
    pass

# or...
from HTMLParser import HTMLParser

class BaseHTMLProcessor(HTMLParser):
    pass[/FONT]
```
It looks like you're trying to inherit from the module, and not the class defined inside the module.

---

### Post by mssever on 2006-11-29
Thanks! I knew it was something simple! I'm just having a hard time not thinking in PHP.

I wonder if you could explain something, though. Why was the error message complaining about too many arguments being passed to __init__, when I didn't pass any arguments at all?

---

### Post by po0f on 2006-11-30
mssever,

I don't know the details, but I guess I could take a stab in the dark.

This is pure conjecture, but I'm pretty sure one of the arguments passed to a module's __init__() is the module's name that's doing the importing.  As for the other one, I have no clue.

Please, if someone more knowledgeable sees this and has the answer, do tell because I'm curious myself.  :)

---

### Post by dwblas on 2006-11-30
> complaining about too many arguments being passed to __init__, when I didn't pass any arguments at all?I don't do much HTML in Python but it looks like it may also be from calling the inherited class incorrectly.  Try it as above and if if the error persists post back.

---

