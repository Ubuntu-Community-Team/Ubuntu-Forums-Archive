---
title: "a bug in python?"
date: 2008-10-23
forum: Programming Talk
---

### Post by ssam on 2008-10-23
I have had strange issue were an imported module gets set to None during the destruction of an object. i have managed to make a minimal test case. is this a bug in python or am i doing something wrong?

```

#!/usr/bin/env python
import shutil
from math import *

class Foo(object):
    def __init__(self):
        print shutil
    def __del__(self):
        print shutil

if __name__ == '__main__':
    print shutil
    a = Foo()

```
outputs
```

<module 'shutil' from '/usr/lib/python2.5/shutil.pyc'>
<module 'shutil' from '/usr/lib/python2.5/shutil.pyc'>
None

```

if i comment out the line "from math import *", then i get

```

<module 'shutil' from '/usr/lib/python2.5/shutil.pyc'>
<module 'shutil' from '/usr/lib/python2.5/shutil.pyc'>
<module 'shutil' from '/usr/lib/python2.5/shutil.pyc'>

```

any ideas?

---

### Post by pp. on 2008-10-23
My hypothesis is that you are seeing side effects of python terminating the execution of your program. It "unassigns" the values of two variables, ***shutils*** and ***a***. Just before dropping the values from those variables, the values are sent the __del__() message. In the first case, shutils appears to be dropped before a, in the second case it appears to be the other way around.

I don't know if the language defines the order in which variables are "unassigned". 

Since the __del__ method is but infrequently used, I see two options for you:
[LIST]
[*]Either the sequence in which the __del__() messages is sent is irrelevant for your purposes: ignore it
[*]Or the sequence is relevant: find the specifications which cover that situation (sorry, that's a thinly veiled RTFM).
[/LIST]

---

### Post by unutbu on 2008-10-23
If you change 

```
if __name__ == '__main__':
    print shutil
    a = Foo()
```

to
```
if __name__ == '__main__':
    print shutil
    a = Foo()
    del a
```
You could also force a to be deleted before shutil, and thereby avoid the problem.

---

### Post by ssam on 2008-10-24
thanks for the hints

i my module i have a class that make temp folders to do work in. it keeps track of them, so that in the __del__() it can clean them up. ideally if the user of the module still has objects left at the end of their program, they should be automatically cleaned up.

I found an ugly work around. for the class to hold a reference to the module, and call that reference during __del__(). but given the subtle change that the 'from math import *' line gives i dont know if this is robust.

```

#!/usr/bin/env python
import shutil
from math import *

class Foo(object):
    def __init__(self):
        self.shutil = shutil
        print self.shutil
    def __del__(self):
        print shutil
        print self.shutil

if __name__ == '__main__':
    print shutil
    a = Foo()
```

---

### Post by ghostdog74 on 2008-10-24
what is it that you want to do that requires you to code up a class? just curious

---

