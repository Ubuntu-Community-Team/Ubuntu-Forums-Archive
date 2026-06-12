---
title: "GCC Header File Not Found Error at Compiling"
date: 2012-12-04
forum: Programming Talk
---

### Post by Coolapple on 2012-12-04
I have several header files in the folder the scripts are as well as in some sub-folders of the higher root folder that I'm using.  

Through CPLUS_INCLUDE_PATH I have indicated the directory destination of the headers that are to be included.

I can see that the path has been included through cpp -v

However when I try to compile the c++ code, it gives me

"fatal error: delay.h : No such file or directory" 

What am I doing wrong?

---

### Post by spjackson on 2012-12-04
It's hard to guess without the details, but I'll have a go.

It could be failure to export CPLUS_INCLUDE_PATH or incorrect choice of separator. However, if cpp -v shows the right path then neither of those possibilities can be it.

I've never used CPLUS_INCLUDE_PATH but the docs say that it has the same effect as -isystem, not -I. Perhaps you are using "..." not <...> when including delay.h?

---

### Post by Coolapple on 2012-12-04
I've tried both "..." and <...> , but the end result was the same. 

What kind of details can I provide to further help to solve the case?

For example, when I put the header files in the same folder, it works.. but then it needs to be in different folders..

---

### Post by steeldriver on 2012-12-04
I'm a bit out of date with this stuff but have you tried using CPPFLAGS?

```
CPPFLAGS += -I/path/to/include/dir
```Also I'm not clear if you are using C or C++? That may affect which variables are applied (C_INCLUDE_PATH for the .c:.o rule, CPLUS_INCLUDE_PATH for the .cpp:.o rule)

---

