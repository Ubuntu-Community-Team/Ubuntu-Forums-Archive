---
title: "Traceback Error - Python"
date: 2008-09-22
forum: Programming Talk
---

### Post by Xavieran on 2008-09-22
Hi,

I'm trying to extract a stack in my program for a format string with traceback.format_stack(), but when I use it (and any of the other related functions in the traceback module) I get this error:

```
Traceback (most recent call last):
  File "<stdin>", line 337, in <module>
  File "<stdin>", line 114, in __init__
  File "<stdin>", line 100, in parse_config
  File "/usr/lib/python2.5/traceback.py", line 271, in format_stack
    return format_list(extract_stack(f, limit))
  File "/usr/lib/python2.5/traceback.py", line 293, in extract_stack
    lineno = f.f_lineno
AttributeError: 'int' object has no attribute 'f_lineno'
```

Any ideas what's wrong?

The application is a curses based problem, but this error happens before curses is instantiated.

---

### Post by wolterh on 2008-09-22
First of all, I recommend you to get an IRC client (xchat), connect to irc.freenode.net, and enter the #python channel when you have any doubt.

Now, clearly 'f' is an 'int' (or natural numeric) object. Apparently, you had some errors while loading whatever f_lineo is. In any case, I cannot provide you more help if you do not post your code, so please do so.

---

### Post by Xavieran on 2008-09-22
Sorry guys...really stupid mistake!!
```

raise ConfigError,'problem with configuration file:%s'%(cfg.name,traceback.format_stack(0))
```

format_stack does not take an int as an argument...

---

