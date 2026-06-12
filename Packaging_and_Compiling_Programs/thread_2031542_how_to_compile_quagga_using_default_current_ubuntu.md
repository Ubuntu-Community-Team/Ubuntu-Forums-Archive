---
title: "how to compile quagga using default current ubuntu compiled package ?"
date: 2012-07-22
forum: Packaging and Compiling Programs
---

### Post by bahramwhh on 2012-07-22
Hi, 
I'm trying to compile quagga from source, I have all dependencies and I get no error during compile and everything goes fine. 
But some files are missing in comparison with current ubuntu compiled package which can be found in the repositories. 
For example "/usr/lib/quagga/" binary packages exist in the official ubuntu package but in my compiled program doesn't exist !

I was wondering how I can compile such that I can have a compiled quagga just like ubuntu offical package ?
what parameters should be passed to ./configure script ?! 

Thanks in advanced.

---

### Post by SevenMachines on 2012-07-22
Are you building a debian package with 
```
$ debuild -b -us -uc
```
If you're compiling a straight build from source (no packaging) then you'll need to look at debian/rules to see what options debian uses to build its package. Look at the override_dh_auto_configure: rule, you'll see lots of --enable parameters that are passed to ./configure

---

