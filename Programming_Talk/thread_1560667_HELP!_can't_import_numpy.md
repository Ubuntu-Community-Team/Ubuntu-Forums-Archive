---
title: "HELP! can't import numpy"
date: 2010-08-25
forum: Programming Talk
---

### Post by qvyang on 2010-08-25
I installed numpy yesterday, it worked fine. Then I upgraded my python 2.6.2 to python 2.6.5. Now when I try to import numpy I get this:

```
Python 2.6.5 (r265:79063, Aug 24 2010, 11:28:27) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named numpy
```

I tried to completely uninstall and then reinstall numpy, but still getting the same error. Could any one help please?

---

### Post by Bachstelze on 2010-08-25
How did you upgrade your Python? The date doesn't match the version in the repos.

---

### Post by qvyang on 2010-08-25
Thanks for the reply. I downloaded the source file and installed it from terminal which fixed the problem.

---

