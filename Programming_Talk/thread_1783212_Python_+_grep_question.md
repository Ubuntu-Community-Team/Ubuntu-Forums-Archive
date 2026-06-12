---
title: "Python + grep question"
date: 2011-06-15
forum: Programming Talk
---

### Post by Sam White on 2011-06-15
How can I define the output of a grep command called from within a .py script as a string?

Here is waht I have ATM, but this returns 0:

article = os.system('grep -o -m 1 [http://bit.ly/](http://bit.ly/)...... "search.atom?q=itfc from:twtduk"')

Any help?

Sam

---

### Post by simeon87 on 2011-06-15
You are getting the program's return status, not its output. You need to capture the output to stdout instead.

Example:

```
import subprocess as sub
p = sub.Popen('ls', stdout=sub.PIPE, stderr=sub.PIPE)
output, errors = p.communicate()
print output
```

---

