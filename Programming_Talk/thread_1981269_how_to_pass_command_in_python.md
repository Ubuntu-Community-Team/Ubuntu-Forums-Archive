---
title: "how to pass command in python?"
date: 2012-05-16
forum: Programming Talk
---

### Post by prismctg on 2012-05-16
How to pass bash command using Python 3.x ?

---

### Post by cmont899 on 2012-05-16
Something like this:

```
import os 
os.system('command')
```

---

### Post by ziekfiguur on 2012-05-17
> **cmont899 said:**
> Something like this:

```
import os 
os.system('command')
```

According to the documentation using the subsystem module is the preferred way.
See [here]("http://docs.python.org/py3k/library/subprocess.html") for information and examples of how to use it.

---

### Post by prismctg on 2012-05-17
Thnx every one

---

