---
title: "apt-get not installing packages fully"
date: 2006-01-15
forum: Repositories &amp; Backports
---

### Post by duffydack on 2006-01-15
after messing around with nxserver i decided to reinstall it.  apt-get remove freenx and also removed any dir i found for it, to start from fresh.  I installed it again but this time the config i wanna edit is not there anymore (/etc/nxserver/node.conf).  What can i do?  

thanks

---

### Post by jasmuz on 2006-01-15
sudo apt-get purge freenx
sudo apt-get install freenx

---

