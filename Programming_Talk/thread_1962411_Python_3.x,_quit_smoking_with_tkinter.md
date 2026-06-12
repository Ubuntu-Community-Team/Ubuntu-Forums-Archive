---
title: "Python 3.x, quit smoking with tkinter"
date: 2012-04-21
forum: Programming Talk
---

### Post by Metul Burr on 2012-04-21
This was my first attempt at python3.x tkinter. Any suggestions?

---

### Post by r-senior on 2012-04-21
I found pylint really helpful in terms of improving my Python code. Actually I found it really annoying at first, but I think it's helped me write more readable and more standard code.

```
$ sudo apt-get install pylint
$ pylint myscript.py
```

It makes suggestions and picks up errors or unused code. For example, you've imported 'sys' but not used it. Or at line 119, you declare 'mysep' but never use it.

Sometimes I find that pylint needs some rules disabling for GUI toolkits, but the manual explains how.

And if you are trying to quit ... good luck. :)

---

