---
title: "Python grep like for urllib"
date: 2010-11-17
forum: Programming Talk
---

### Post by ard1an on 2010-11-17
Hi, I need something like grep for a python script

```
import urllib
f = urllib.urlopen("http://www.ubuntu.com")
print f.read()
```

So I need to search for specific string, how do I do that ive got some suggestion to use lxml.html dunno how to use it.

---

### Post by Vaphell on 2010-11-17
what about re.search()?

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

---

