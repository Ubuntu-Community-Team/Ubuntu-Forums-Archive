---
title: "[Python] Mechanize module 'open' attribute doesn't work"
date: 2008-10-25
forum: Programming Talk
---

### Post by ratmandall on 2008-10-25
```
>>> from mechanize import Browser
>>> Browser.open("http://google.com")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unbound method open() must be called with Browser instance as first argument (got str instance instead)
```

What does this mean and how do I get it to work?
thanks.

---

### Post by geirha on 2008-10-25
It means you must run open on an instance, not the class. Do help(Browser) to see what arguments the constructor needs, then create an instance ```
b= Browser(...)
b.open("...")
```

---

