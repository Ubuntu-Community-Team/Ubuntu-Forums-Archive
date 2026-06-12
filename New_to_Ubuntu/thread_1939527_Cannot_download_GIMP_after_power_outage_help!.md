---
title: "Cannot download GIMP after power outage help!"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by tefl0n on 2012-03-11
I was installing the GIMP package and optional addons, when the power went out.

Turned the computer back on, and I'm unable to download the application! I'm using the Ubuntu software centre, and 11.10.

Here is the message I got.

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Not sure where to go with this, or how to fix the packages.. is there an easy way to remove these packages and re-install? 
I'm not able to download anything using the software center anymore..

Thanks!!

---

### Post by Krytarik on 2012-03-11
> **tefl0n said:**
> SystemError: E:I wasn't able to locate a file for the **ttf-mscorefonts-installer** package. This might mean you need to manually fix this package.
Please see this guide:

[http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html](http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html)

Regards.

---

### Post by tefl0n on 2012-03-11
Thanks for the links. Command to fix did not work but used sudo get the package again. Fixed!

---

