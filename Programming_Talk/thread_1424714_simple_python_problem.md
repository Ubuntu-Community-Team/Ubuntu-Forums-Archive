---
title: "simple python problem"
date: 2010-03-08
forum: Programming Talk
---

### Post by ikt on 2010-03-08
.

---

### Post by Some Penguin on 2010-03-08
One thing that strikes this non-Python-programmer:

You parse an XML file (presumably resulting in 'tree' containing the DOM)... and then you take the DOM and turn it back into a string using tostring(), for searching.   Seems to me that either you should use the DOM for searching, or not build it if you're not going to use it.

---

### Post by ikt on 2010-03-08
Cheers to Some Penguin and Yhg1s :)

[01:48] <Yhg1s> ikt: both tree.find('api') and tree.findall('api') work fine here.
[01:48] <Yhg1s> ikt: do run it on the ET tree, not the string you get from ElementTree.tostring.

---

