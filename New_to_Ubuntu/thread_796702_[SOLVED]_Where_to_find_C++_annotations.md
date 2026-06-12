---
title: "[SOLVED] Where to find C++ annotations?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-16
I installed the package C++ annotations . Now, How how can I read it,  I don't know where the files are stored ? 

Also is there a similar package for C language in synaptics?

Many thanks in advance.

---

### Post by diaa on 2008-05-16
> **bhadotia said:**
> I installed the package C++ annotations . Now, How how can I read it,  I don't know where the files are stored ? 


You can see the files installed by any package by running the command
```
 dpkg -L <package_name>
```so in this case you should run
```
dpkg -L c++-annotations
```for me I installed c++-annotations-pdf and it can be found in 
```
/usr/share/doc/c++-annotations/cplusplus.pdf
```> **bhadotia said:**
> 
Also is there a similar package for C language in synaptics?

Many thanks in advance.

For C I think you should check the package
```
c-cpp-reference
```

---

### Post by bhadotia on 2008-05-17
Thanks!

---

