---
title: "What does this mean - getting error when I try and install"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by Brian_O_Neill on 2014-01-08
sudo add-apt-repository ppa:nilarimogard/webupd8
[sudo] password for brian: 
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 3, in <module>
    import os
ImportError: No module named os
brian@brian-DOTS-E2:~$

---

### Post by Hexxus on 2014-01-08
Hey there,

I'm not entirely sure. I've seen strange issues with corrupt images and such when they're burned to CD or on a flash drive. Try a different usb drive or burning it to a cd to see if it persists.

Also, which version was this? 12.04? 13.10? 32bit, 64bit? etc... More info the better.



*** Sorry - by install I thought this was a fresh install. ***

---

### Post by mc4man on 2014-01-08
likely for the same reason you get/got this
[http://ubuntuforums.org/showthread.php?t=2177836&p=12803592#post12803592](http://ubuntuforums.org/showthread.php?t=2177836&p=12803592#post12803592)

Have you removed, replaced or installed a different version of python or had a python update fail?

(plus you appear to be using 10.10 which is long since 'end of life'

---

