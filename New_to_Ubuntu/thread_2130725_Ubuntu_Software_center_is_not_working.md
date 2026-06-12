---
title: "Ubuntu Software center is not working"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by BSG Fan on 2013-03-30
I can not download (since today) any single update or software.
help.

[I]An unhandlable error occured
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 972, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1096, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the libkexiv2-10 package. This might mean you need to manually fix this package.[/I]

and I meant no single software in any category.

---

### Post by ManamiVixen on 2013-03-30
Try sudo apt-get update && sudo apt-get dist-upgrade

That may fix the package in an update.

---

### Post by BSG Fan on 2013-03-30
> **ManamiVixen said:**
> Try sudo apt-get update && sudo apt-get dist-upgrade

That may fix the package in an update.

ManamiVixen:
Thank you so much!
It is working now.
Have a great Ubuntu day
:P

---

