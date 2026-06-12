---
title: "PHP segmentation faults"
date: 2007-04-10
forum: Programming Talk
---

### Post by counterpoint on 2007-04-10
I'm developing a PHP system and currently trying to transfer my work to a machine running Ubuntu 6.10.  Things are pretty much at a halt because of this problem.

In certain configurations of the code (the ones that include the features needed) there is no output to the browser, and PHP appears to have failed.  There is a record in the Apache error log along the lines of :

[Tue Apr 10 09:41:54 2007] [notice] child pid 9056 exit signal Segmentation fault (11)

The error can be tracked down, but since it occurs between the last line of a method and the line following the method call, there is nothing I can do about it.  I've tried a variety of ways to implement the feature (error logging) none of which seem able to evade the problem.  I have no idea what causes it.

Other frustrating features of the problem are that the code can be run in debug mode in Zend Studio without any fault occurring, and the code can also be installed in a remote site and will run correctly.  But without local testing, development is drastically slowed down.

Any suggestions?

---

### Post by 1tiger1 on 2007-04-17
Just curious, 

At what point is PHP crashing? during startup? while running a script?

---

### Post by counterpoint on 2007-04-18
During the running of a script (or, rather, an extensive set of scripts running to thousands of lines).  But so far as source level debugging goes, the fault occurs between one statement and the next.

---

### Post by 1tiger1 on 2007-04-18
> **counterpoint said:**
> During the running of a script (or, rather, an extensive set of scripts running to thousands of lines).  But so far as source level debugging goes, the fault occurs between one statement and the next.

That means it would be rather difficult then to figure out which line is the problem child. PHP segmentation faults (in my experience) typically stem from a module installed incorrectly or a corrupted library accessed by a specific function. By chance is there any way to isolate the function that may be running?

---

