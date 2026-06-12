---
title: "update manager error"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by urvaksh on 2008-05-31
When I try and update via update manager I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This error message began showing up yesterday after, I think, my computer shut down (the battery ran out) during an routing update.

Is there a quick fix for this so I can get updates. Am a relative noobie, FYI
Thanks

---

### Post by Maestro23 on 2008-05-31
Open a terminal and type the following:

> sudo dpkg --configure -a

Then:

> sudo apt-get update

sudo apt-get upgrade


---

### Post by urvaksh on 2008-06-01
It worked.
Thank you.

---

