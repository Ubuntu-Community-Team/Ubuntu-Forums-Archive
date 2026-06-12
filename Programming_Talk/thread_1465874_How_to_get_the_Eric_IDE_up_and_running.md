---
title: "How to get the Eric IDE up and running?"
date: 2010-04-29
forum: Programming Talk
---

### Post by khackbarth on 2010-04-29
Eric has several prerequisites including Python, Qt, PyQt, and QScintilla.  It's not clear to me if these prerequisites have to already be installed at the time Eric is installed.
 
I believe that all of these are available via the Ubuntu Software center.
 
I'd love a tutorial describing what to install in what order so that all the pointers in Eric to these prerequisites are defined properly and so that help for each of the prerequisites works.
 
Thanks,
Ken

---

### Post by solar george on 2010-04-30
eric is in the [repos]("apt://eric") 
If you really need to install from the website you can use:
```
apt-get build-dep eric
```
from a terminal to install the dependancies.

---

