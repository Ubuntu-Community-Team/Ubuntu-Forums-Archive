---
title: "Python problem inheriting metaclass"
date: 2006-01-15
forum: Programming Talk
---

### Post by David Marrs on 2006-01-15
So I finally decided to try this python thing you all keep going on about! :p

I've been trying to inherit a class (that I've called "player") from xmms.control, which itself turns out to be a metaclass.

A simple script:
```
from xmms import control
class hello:
  __metaclass__ = control
  def hellomethod(self): print "hello"

hello().hellomethod()
```
produces the following error:
```
Traceback (most recent call last):
  File "hello.py", line 2, in ?
    class hello:
TypeError: Error when calling the metaclass bases
    'module' object is not callable
```

I'm presuming that xmms.control is a metaclass because if I try inheriting it with the line "class player(control):", I get error messages relating to metaclasses. Can anyone tell me what I'm doing wrong?

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=David Marrs]So I finally decided to try this python thing you all keep going on about! :p

I've been trying to inherit a class (that I've called "player") from xmms.control, which itself turns out to be a metaclass.

A simple script:
```
from xmms import control
class hello:
  __metaclass__ = control
  def hellomethod(self): print "hello"

hello().hellomethod()
```
produces the following error:
```
Traceback (most recent call last):
  File "hello.py", line 2, in ?
    class hello:
TypeError: Error when calling the metaclass bases
    'module' object is not callable
```

I'm presuming that xmms.control is a metaclass because if I try inheriting it with the line "class player(control):", I get error messages relating to metaclasses. Can anyone tell me what I'm doing wrong?[/QUOTE]
I don't have the package installed that you are using, but from the error message you are getting, I would guess that xmms.control is a module rather than a class.  Try doing:
```

>>> import xmms.control
>>> help(xmms.control)

```
from the python prompt.

As a last ditch effort
```

>>> import xmms.control
>>> type(xmms.control)

```
should tell you what type of object control is.  If it is a metaclass, I would be surprised if there weren't any docs explaining its use.

---

### Post by David Marrs on 2006-01-17
thanks. Is a metaclass the same thing as a module?

I was making the mistake of thinking that methods must belong to classes when they can actually both belong to a module independantly of one another.

---

### Post by cwaldbieser on 2006-01-17
[QUOTE=David Marrs]thanks. Is a metaclass the same thing as a module?

I was making the mistake of thinking that methods must belong to classes when they can actually both belong to a module independantly of one another.[/QUOTE]
No, a metaclass is a factory for making other classes.  The concept is a little out there-- I find that I don't really use them in Python that much.

A module in Python is a convenient place to define names where they won't interfere with other names.

---

