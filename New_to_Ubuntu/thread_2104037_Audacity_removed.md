---
title: "Audacity removed"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by TheManno1 on 2013-01-11
To be installed
libsbsms10

audacity:
  Depends: audacity-data (=2.0.2+svn20130110+r7499-0~r19~precise1) but 2.0.2+svn20130110+r7501-0~r19~precise1 is to be installed

Ubuntu 12.10 64 bit

---

### Post by tlhIngan on 2013-01-11
Umm..., you want to elaborate on that a little bit?
What the issue?

---

### Post by TheManno1 on 2013-01-12
Can't re-install it using synaptic. That error above comes.

---

### Post by zombifier25 on 2013-01-12
You're probably using the Audacity daily build PPA, the Precise version on your Quantal box.
If so, purge it using ppa-purge. Install it first:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:audacity-team/daily
sudo apt-get update
```

---

