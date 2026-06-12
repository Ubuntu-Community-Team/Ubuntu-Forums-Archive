---
title: "Qt creator eats 100% CPU on 10.04"
date: 2010-05-04
forum: Programming Talk
---

### Post by juzzlin on 2010-05-04
I updated my system to 10.04 recently and now noticed, that Qt Creator (installed from the Software Center) is eating 100% CPU and it takes tens of seconds to start it. Is anyone else having this same issue?

ii  qtcreator                             1.3.1-1ubuntu1                                  lightweight integrated development environme


Edit: 

This is a known issue: 
[https://bugs.launchpad.net/ubuntu/+source/qtcreator/+bug/517364](https://bugs.launchpad.net/ubuntu/+source/qtcreator/+bug/517364)

Workaround is to start Qt Creator like this:
'qtcreator -noload Help'

---

### Post by maryjane136 on 2010-05-09
Reinstall the Qt SDK. 
I work with 4.6.2.

---

