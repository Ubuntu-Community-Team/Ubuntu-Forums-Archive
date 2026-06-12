---
title: "An unhandlable error occured"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by bundimartin on 2011-11-14
Hi team, am new to Ubuntu and just installed Ubuntu 11.10 and some applications then got an error that is now preventing me from installing other applications in Ubuntu software center. The error is:

**an unhandlable error occured**
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Kindly help me fix this problem, I'll b much grateful.

Regards,

Pompi

---

### Post by bundimartin on 2011-11-14
Thanks fossfreedom. I have read a post you made and it has helped me solve the problem. 

**Solution:**
Try running the following in a terminal session:
sudo dpkg --configure -a sudo apt-get update sudo apt-get upgrade

When you see in the terminal window appear  "Package configuration - 
  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;" 
  

press tab key until the "OK" is highlighted. 



  Then press Enter to accept the license agreement




Great!

---

### Post by ndimmick on 2011-12-20
bundimartin,

Thank you so much for this solution.  I goobered up my software center by not knowing how to accept the license agreement from Microsoft.  I ended up quitting during that process, which rendered software center unable to install anything. This fixed it for me!

---

