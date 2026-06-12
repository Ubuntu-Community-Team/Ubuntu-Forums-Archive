---
title: "Learn Python 3?"
date: 2008-12-15
forum: Programming Talk
---

### Post by chris062689 on 2008-12-15
Are there any tutorials out yet on how to learn Python 3.0?

---

### Post by mssever on 2008-12-15
> **chris062689 said:**
> Are there any tutorials out yet on how to learn Python 3.0?
On the Python website, you can find a summary of the differences between Python 2.6 and Python 3.0. That's really all you need. Python 3.0 isn't all that different, really.

---

### Post by pmasiar on 2008-12-15
Can please some mod add previous discussion about Python 3K to stickies? It's getting boring to have it twice a week... :-/

---

### Post by jimi_hendrix on 2008-12-15
semi-OT question:

is there a python standard? or do people just code in whatever version they like (2.4, 2.5 2.6, 3.0...)

---

### Post by mssever on 2008-12-15
> **jimi_hendrix said:**
> semi-OT question:

is there a python standard? or do people just code in whatever version they like (2.4, 2.5 2.6, 3.0...)
My not-very-well-informed opinion is that you should use the latest version your users can be reasonably expected to have. Since Intrepid uses 2.5, and since I don't care too much about other distros, I use 2.5. I'll continue using whatever version Ubuntu uses by default. Others might not have the luxury of following such a simplistic policy.

---

### Post by slavik on 2008-12-15
> **mssever said:**
> My not-very-well-informed opinion is that you should use the latest version your users can be reasonably expected to have. Since Intrepid uses 2.5, and since I don't care too much about other distros, I use 2.5. I'll continue using whatever version Ubuntu uses by default. Others might not have the luxury of following such a simplistic policy.
There are also systems that are of the 2003 era, which have only 2.4

---

### Post by Greyed on 2008-12-16
> **jimi_hendrix said:**
> is there a python standard? or do people just code in whatever version they like (2.4, 2.5 2.6, 3.0...)

Not really, no.  However unless you're doing some deep magic most of Python is backwards compatible.  I still have 1.5.2 era scripts that run fine on 2.6.  By the same token it is also decently forward compatible as well.  Right now I program for a mix of 2.4, 2.5 and 2.6 and really don't think of which version I am on.

The real break is from 2.x to 3.0 as that is intended to break backwards compatibility to clean up the language a bit.  print "foo" becoming print("foo") being the biggest culprit.

---

### Post by jimi_hendrix on 2008-12-16
ignore

---

### Post by wmcbrine on 2008-12-16
> **jimi_hendrix said:**
> is there a python standard?There is no formal standard. CPython is the reference implementation which sets the de facto standard.

---

### Post by fiddler616 on 2008-12-16
> **pmasiar said:**
> Can please some mod add previous discussion about Python 3K to stickies? It's getting boring to have it twice a week... :-/
+1
It won't even have to be permanent--just until most people have settled in.

---

### Post by Greyed on 2008-12-16
I'm not sure if that is still the case.  There does exist a language reference independent of CPython: [http://docs.python.org/reference/index.html](http://docs.python.org/reference/index.html)

---

### Post by mssever on 2008-12-16
> **wmcbrine said:**
> There is no formal standard. CPython is the reference implementation which sets the de facto standard.
If my understanding is correct, PEPs are the standard in the areas they cover. Presumably everything will eventually be covered by PEPs.

---

### Post by pmasiar on 2008-12-16
> **Greyed said:**
> I'm not sure if that is still the case.  There does exist a language reference independent of CPython: [http://docs.python.org/reference/index.html](http://docs.python.org/reference/index.html)

Yes, but as developers of Jython, PyPy, and IronPython found, that reference is written by humans, so fallible. Some (very obscure) features are just quirks of CPython implementation, and were not reimplemented in Jython or ironPython - so ie. extra efforts are needed for Django to run on Jython - but it can, and was, done.

---

