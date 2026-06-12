---
title: "The python way to do things"
date: 2013-06-26
forum: Programming Talk
---

### Post by abraxas334 on 2013-06-26
Hi everyone,
just a quick question as to how I would do something like this the python way, i.e. avoiding the for loop:

[PHP]
#import numpy as np

a = np.array([0,4,4,5,6,5,6,0,0,4,5,0,6])
for i in range(len(a)):
     if a[i]>0:
          a[i]=a[i]-3

print a

[/PHP]

Thanks for the help!

---

### Post by steeldriver on 2013-06-26
[DISCLAIMER: I am NOT a python programmer] something like this maybe?

```

>>> a = [ v-3 if v > 0 else v for v in a ]
>>> a
[0, 1, 1, 2, 3, 2, 3, 0, 0, 1, 2, 0, 3]

```

---

### Post by ssam on 2013-06-26
as you are already using numpy (which is a good thing to use on arrays of numbers), you can use numpy slicing

```

import numpy as np
a = np.array([0,4,4,5,6,5,6,0,0,4,5,0,6])
a[a>0] -= 3

```

the [a>0] selects the items where the condition is true, then the -= subtracts from their current value.

array operations in numpy are much faster than loops. if you are needing even more performance on large arrays look at numexpr.

Also note that you should not put a '#' on the import statement. the '#' indicates a comment in python.

---

