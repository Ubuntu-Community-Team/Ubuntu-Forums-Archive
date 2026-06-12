---
title: "Compile a Netbeans C++ project from command line"
date: 2011-09-08
forum: Packaging and Compiling Programs
---

### Post by erotavlas on 2011-09-08
Hi,

I would like to know how can I compile a C++ project made with Netbeans from the command line of a generic computer. If I try to compile the project from my computer (where the project has been developed) by using the command make, then I can complete the compilation with success.

From the main folder of Netbeans project: 
```
make -f Makefile CONF=Debug(Release)
``` 

But If I repeat the same procedure from a generic computer, it doesn't work because the path of the project is different.
A brutal and very slow solution it is to change all the path from the Makefile. Do you know if exist a better solution?

Thank you

---

