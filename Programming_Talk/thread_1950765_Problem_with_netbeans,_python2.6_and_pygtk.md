---
title: "Problem with netbeans, python2.6 and pygtk"
date: 2012-04-01
forum: Programming Talk
---

### Post by Lord_JABA on 2012-04-01
the problem is:
when i run python interactive console in terminal and type ```
import pygtk
``` it works OK put when i run file containing it in netbeans7 i got ```
ImportError: No module named pygtk
```
I already swiched from Jython to Python2.7.2+
add every dir under /usr/lib/python2.7/dist-packages to Python Path
so why the difference?

Edit:
I do in the good working python from console:
```

import sys
for path in sys.path:
    print('"%s"' %path)

```
and pasted result to netbeans Python path but still cant use import on most libraries

---

