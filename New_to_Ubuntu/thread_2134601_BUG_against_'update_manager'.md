---
title: "BUG against 'update manager'"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by Ybigras on 2013-04-11
Hello,
 
this is my first install of Ubuntu 12.04 64 bit I have run into an error while trying to perform updates. The error message prompted me to post into the support forum for assistance.

Here is the error that the 'update-manager' produces when i try to perform updates: 'E:Malformed line 60 in source list /etc/apt/sources.list (dist parse)' 

After that  the 'update-manager' automatically exits out.

any advice?

-Yannick

---

### Post by ajgreeny on 2013-04-11
Can you show us the output of ```
cat /etc/apt/sources.list
```Line 60 of that file must have something that has the wrong syntax and that line needs editing or deleting to be able to be read properly.

---

