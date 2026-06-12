---
title: "no connection to update"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by atilay2k on 2015-05-05
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease

---

### Post by Bucky Ball on 2015-05-05
Welcome. Open a terminal and issue these commands, one after the other, and hitting return after each:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```	

Post any and all errors. Thanks.

Did you manually install the repo that is giving the error? If so, open Software and Updates (may be something different in your release) and disable or remove it.

---

