---
title: "creating python modules from Pascal"
date: 2009-06-04
forum: Packaging and Compiling Programs
---

### Post by vancheese on 2009-06-04
Hi People

I'm running Jaunty 64bit and I'm trying to use this most amazing tutorial in using Pascal/Dephi to create modules for python.

[http://wiki.lazarus.freepascal.org/Developing_Python_Modules_with_Pascal](http://wiki.lazarus.freepascal.org/Developing_Python_Modules_with_Pascal)

However, When following the tutorial, the complying of the module by Lazarus fails when it comes to the linking of the pascal module.

 Linking PyMinMod.so
 /usr/bin/ld: Python: No such file: No such file or directory


I've installed all the python development files and this is beyond my knowledge and I've no idea about ld and linking ... Can anyone offer some help?

Thanks 

Andy

---

### Post by PeterBBB on 2009-06-04
Case sensitivity? Linux does not have a 'Python' package, it has 'python'.

---

### Post by vancheese on 2009-06-08
No joy with changing the case, the problem seems to originate from the free pascal compiler

Lazurus uses this command

fpc  -MDelphi -Cirot -O1 -gl -XX  -k-framework -kpython -WG -vewnhi -l -Fu. -oPyMinMod.so PyMinMod.dpr

and the errror orriginates with -k-framework -kpython section

---

### Post by vancheese on 2009-06-15
I've solved this problem by removing the framework options, this transpires only to be a Mac OsX thing.

If you are on a 64 bit version of ubuntu, you'll find that the compiled module will break with the following error

ImportError: PyMinMod.so: undefined symbol: Py_InitModule4


To sort this out, edit PyApi.pas and replace Py_InitModule4 with Py_InitModule4_64

This change is 64 bit v 32 size type issues

---

