---
title: "[SOLVED] Python library import"
date: 2008-09-12
forum: Programming Talk
---

### Post by kjohansen on 2008-09-12
Im confused on how importing libraries works.

I am trying to work with scipy

If I do

```

import scipy
print scipy.stats.mean([1,2,3,4]);

```

I get:

```

Traceback (most recent call last):
  File "/home/johank/untitled-1.py", line 5, in <module>
    print scipy.stats.mean([1,2,3,4]);
AttributeError: 'module' object has no attribute 'stats'
Process terminated with an exit code of 1

```


but if I do:

```

import scipy
import scipy.stats

print scipy.stats.mean([1,2,3,4]);

```

it works.

Why do I have to import scipy.stats as a separate line.  I would expect that scipy.stats is a child and should be imported with scipy. I know I could do "from scipy import *", but I was warned against this by our friend pmasiar in a previous thread.  Is this how it is supposed to be? Can I use one import to import the module and all its child modules?

---

### Post by imdano on 2008-09-12
You should be able to do ```
from scipy.stats import mean
``` or even ```
import scipy.stats as stats
```without importing scipy first.

---

### Post by pmasiar on 2008-09-12
> **kjohansen said:**
> Why do I have to import scipy.stats as a separate line.  I would expect that scipy.stats is a child and should be imported with scipy. ...Can I use one import to import the module and all its child modules?

You expectations are still off. Read "Zen of Python", enter import this in Python shell. One of the rules is: "explicit is better than implicit". If you want children, you need to import them explicitly. 

Reason is same as why "from scipy import *" is wrong: you will lose control which names are injected to your app namespace. You want to have full control which name comes from where (because of dynamic typing).

---

