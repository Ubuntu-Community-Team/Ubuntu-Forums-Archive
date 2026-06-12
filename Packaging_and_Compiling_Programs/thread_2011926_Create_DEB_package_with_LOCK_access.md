---
title: "Create DEB package with LOCK access"
date: 2012-06-28
forum: Packaging and Compiling Programs
---

### Post by Ravi Amlani on 2012-06-28
Hi All,

This is my very first post on this forum :)
well, I've created one DEB package by maintaining all the standards. It has one large script too, postinst.

Now as we know that Any package can not be installed if "UpdateManager, aptitude OR synaptic" is running. Reverse is also true as we know.
Now, I want to make a package that can aquire a lock from any of these process. 

According to my Research, OS checks for this itself before it executes any file of my package and gives pop up. So if I put PREINST script then also it does not run, obviously.

So what can I do if I want to come over this situation - I want to kill other process (not manually,externally) by my package and let it be install ?

---

