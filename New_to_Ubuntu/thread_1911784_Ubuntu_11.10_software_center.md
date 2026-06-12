---
title: "Ubuntu 11.10 software center"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by GregD001 on 2012-01-19
I just installed ubuntu 11.10.
I am having problems installing software from the software center.

When I select to install something, I get this message

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.



Any ideas?
thank you

---

### Post by ubudog on 2012-01-19
Try this, then repeat what you were doing.  Let us know if it works:
```
sudo apt-get install ttf-mscorefonts-installer
```

Hope that helps,
ubudog

---

### Post by kc1di on 2012-01-19
I still like synaptic better so I always install it.

```
sudo apt-get install synaptic
```

---

### Post by ubudog on 2012-01-19
> **kc1di said:**
> I still like synaptic better so I always install it.

```
sudo apt-get install synaptic
```

Synaptic is a good tool, might come with Ubuntu (not sure about the later versions).

---

### Post by kc1di on 2012-01-19
> **ubudog said:**
> Synaptic is a good tool, might come with Ubuntu (not sure about the later versions).
it's not in 11:10 you must install it.
Dave

---

### Post by raja.genupula on 2012-01-19
hi i actually seen this kind of errors months ago . I think the solution is first you have to re install that problematic font package by removing it .use synaptic to remove completely . I think there it will marked as installed but check for removal and then reinstall it .


All the best .

---

