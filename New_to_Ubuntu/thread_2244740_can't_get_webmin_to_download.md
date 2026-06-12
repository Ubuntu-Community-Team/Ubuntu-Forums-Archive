---
title: "can't get webmin to download"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by Monica_Grote on 2014-09-18
I am having problems installing webmin.  It keeps coming up with error messages.

---

### Post by sandyd on 2014-09-18
> **Monica_Grote said:**
> I am having problems installing webmin.  It keeps coming up with error messages.

======
Moved to New to Ubuntu
======

What error messages are you getting?

Webmin requires some dependencies that are not installed by default on Ubuntu, after running dpkg to install Webmin, you can run
```

sudo apt-get -f install
```
to install the missing packages and to finish the webmin installation.

Side Note:
Webmin is highly insecure and should be secured by the use of a firewall/etc

---

