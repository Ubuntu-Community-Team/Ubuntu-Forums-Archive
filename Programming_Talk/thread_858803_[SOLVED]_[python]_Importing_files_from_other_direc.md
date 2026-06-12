---
title: "[SOLVED] [python] Importing files from other directories?"
date: 2008-07-13
forum: Programming Talk
---

### Post by -grubby on 2008-07-13
How do you import python files from other directories?

---

### Post by ghostdog74 on 2008-07-13
if you have gone through the official python tutorial, you would have found [this]("http://docs.python.org/tut/node8.html"), and solve your problem
```

import sys
sys.path.append('/mydirwherescriptis')
import myownmodule

```
Read and practice the whole tutorial

---

### Post by -grubby on 2008-07-13
Wow, I remember seeing that page when googling. Good job to me for completely looking that part over.

---

