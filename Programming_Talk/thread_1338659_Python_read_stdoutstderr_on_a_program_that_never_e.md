---
title: "Python read stdout/stderr on a program that never ends"
date: 2009-11-26
forum: Programming Talk
---

### Post by loki_dre on 2009-11-26
In python: How do I read stdout or error for a program that doesn't normally end

can i set a timeout for reading?...I would like to get the data read at the end of the timeout


My Code so far is as follows:
```
import sys
import string
import glob
from subprocess import *


item = 'wvdial Modem=/dev/ttyUSB2'
pusb = Popen(item,shell=True, stdout=PIPE, stderr=PIPE, close_fds=True)
ousb = pusb.communicate()[1]
print ousb
```

---

