---
title: "Python 2.7 (win) and threads"
date: 2010-11-27
forum: Programming Talk
---

### Post by Cheesehead on 2010-11-27
I'm writing a Python script that pulls information from QuickBooks and formats it as pretty documents in OpenOffice.

I can start both applications headless, but the wait time (up to 10 sec) is annoying. Since both are headless, they don't consume a lot of CPU (even during startup), but each does require a couple seconds before it will accept connections. Can I use threads to speed up the process? Is that wise?

Currently I do it sequentially:```

import time

print('Opening QB...')
start_quickbooks()
time.sleep(5)
qb = connect_to_quickbooks()

print('Opening OO...')
start_openoffice()
time.sleep(3)
oo = connect_to_openoffice()

print('Ready to start work')

```

Anybody have a simple threading example I can play with?

---

### Post by samjh on 2010-11-28
You probably don't need threads, and it's not likely to help you very much since the bottleneck (establishing connection) is actually outside your code.  Also, Python doesn't have native threads, so parallel code isn't really parallel in Python (there is the multiprocessing module which allow for creating and synchronising multiple processes, but that's probably overkill for your purpose). 

Having said that, your two sleep times seem redundant.  Perhaps you should try this:
```
import time

start_quickbooks()
start_openoffice()
time.sleep(5)
qb = connect_to_quickbooks()
oo = connect_to_openoffice()

print('Ready to start work')
```That will cut your sleep time in half.

---

