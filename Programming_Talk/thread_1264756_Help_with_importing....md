---
title: "Help with importing..."
date: 2009-09-12
forum: Programming Talk
---

### Post by Pyro.699 on 2009-09-12
Hey

I have a folder named **/Foo** and within that folder are 2 files... one is **__init__.py** and the other is **bar.py**.

**__init__.py** contains:
[php]
import os, threading

for module in os.listdir(os.path.dirname(__file__)):
    if module == '__init__.py' or module[-3:] != '.py':
        continue
    __import__(module[:-3], locals(), globals())
del module
[/php]**bar.py** contains:
[php]
class Test(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
        
    def x(self):
        print "Foo Bar"
[/php]Now in the parent directory there is another file called **runMe.py**, it contains:
[php]
import threading
from Foo import *

t = Test()
t.x()
[/php]Now ill get an error because i didn't import threading in **bar.py**. Is there any way that i can get this to work because the threading module was still imported in the main file (**runMe.py**). In reality there are about 40 modules and it would be much much easier if i was able to only include the threading module in the main script.

Thanks
~Cody Woolaver

---

### Post by Pyro.699 on 2009-09-12
Here an example that would be easier to work on (in the rar below).

I basically need to be able to run **bar()** and have the variables that are defined above, carry on.

Thanks
~Cody Woolaver

---

