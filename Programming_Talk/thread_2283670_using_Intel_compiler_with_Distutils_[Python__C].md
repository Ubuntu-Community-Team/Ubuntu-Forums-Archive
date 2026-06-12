---
title: "using Intel compiler with Distutils [Python / C]"
date: 2015-06-23
forum: Programming Talk
---

### Post by bram7 on 2015-06-23
Hello,

When I run setup.py using the command 'python setup.py install --user' the gcc compiler is used by default when C code is compiled. I would like to use the intel compiler. I figured out that when I create distutils.cfg inside the distutils directory and add the following lines:

```

[build]
compiler = icc

```

then setup.py tries to compile using icc. But it gives me the following error message:

"error: don't know how to compile C/C++ code on platform 'posix' with 'icc' compiler". 

I get the same error message if I do 'compiler=intel', just with 'icc' replaced by 'intel'. 
The icc compiler can be found when I type 'which icc' for instance. Could someone please give me a hint how to get it to work correctly ? 
I've been googling for the answer for a very long time, but have not been able to find anything that works for me. 

EDIT: I'm using the python binary from Anaconda (convenient, installs python, numpy, scipy etc). Does it matter which compiler was used to build python ?

sincerely
Bram

---

