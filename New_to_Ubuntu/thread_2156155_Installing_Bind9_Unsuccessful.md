---
title: "Installing Bind9 Unsuccessful"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by wizzy886 on 2013-06-20
Bind9 decides to not install as it is "Unable to find some of the archives". I install it in the usual way of sudo apt-get install bind9. What am I doing wrong and please bear in mind I am a new user.

---

### Post by Doug S on 2013-06-20
What version of Ubuntu are you running? Example of how to check:```
doug@doug-64:~/config/ssh$ [COLOR=#ff0000]cat /etc/lsb-release[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
doug@doug-64:~/config/ssh$ [COLOR=#ff0000]uname -a[/COLOR]
Linux doug-64 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by wizzy886 on 2013-06-21
> **Doug S said:**
> What version of Ubuntu are you running? Example of how to check:```
doug@doug-64:~/config/ssh$ [COLOR=#ff0000]cat /etc/lsb-release[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
doug@doug-64:~/config/ssh$ [COLOR=#ff0000]uname -a[/COLOR]
Linux doug-64 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

13.04

---

### Post by Doug S on 2013-06-22
Try making sure everything is up to date:```
sudo apt-get update
sudo apt-get dist-upgrade
``` then try again. If you still have troubles try adding --fix-missing. If you still have troubles please post the actual related error messages.

---

