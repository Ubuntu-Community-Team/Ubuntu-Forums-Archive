---
title: "gdb STL pretty printing"
date: 2011-06-27
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2011-06-27
Hi,
I am trying to get the debugging STL pretty printing working on my ubuntu install.  I tried to set it up the exact same way I did at work on RHEL, but it is not working.  Has anyone instructions to set this up, or another way to get STL containers to display nicely for a dubugger (preferably that can be used with an IDE like Code::Blocks or Kdevelop)?

[http://sourceware.org/gdb/wiki/STLSupport](http://sourceware.org/gdb/wiki/STLSupport)

is the instructions that I tried to follow.


edit:: when I try to import gdb from python, I get that the module isnt found:
```
jeff@kokiri-forest:~$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gdb
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named gdb

```




Thanks,
Jeff

---

### Post by mourt on 2011-12-20
I'd suggest to use Qt Creator where gdb/python based pretty printing works without any manual setup.

---

### Post by MadCow108 on 2011-12-20
it works fine here (oneiric gcc 7.3) do you get any error message?

if you can't get it to work use the second bullet on that page that works quite good too without python.

---

