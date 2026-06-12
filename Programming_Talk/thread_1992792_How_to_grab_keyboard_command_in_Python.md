---
title: "How to grab keyboard command in Python ?"
date: 2012-05-31
forum: Programming Talk
---

### Post by prismctg on 2012-05-31
How to grab keyboard command in Python 3.x ? I want to grab some keyboard command like ctrl+x , F9 etc in my program

---

### Post by hailholyghost on 2012-06-10
I'm not sure what you mean.

If you mean when executing a python program at the command line, e.g.

```
$python 23
```

a sample script would look like:

```
#!/usr/bin/python
import sys
import math

i = float(sys.argv[1])
i = i/4
print i
j = float(4)/7
print j
```
where "sys.argv[1]" is the first argument passed to the command.

Is that what you mean?

---

### Post by prismctg on 2012-06-11
no, I just want to capture keyboard command like  ctrl+x in my program .example: If I press ctrl+x program do some job .

---

### Post by overcast on 2012-06-12
So you want to capture hotkeys? Like say ALT or CTRL+P sort?

You can check the pykeylogger.

[http://pykeylogger.wiki.sourceforge.net/](http://pykeylogger.wiki.sourceforge.net/)

---

