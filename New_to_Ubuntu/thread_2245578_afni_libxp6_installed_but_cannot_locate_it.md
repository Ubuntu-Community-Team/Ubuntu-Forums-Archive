---
title: "afni libxp6 installed but cannot locate it"
date: 2014-09-24
forum: New to Ubuntu
---

### Post by CarryOn on 2014-09-24
Dear Forum,
I have installed afni on a Ubuntu server (that uses Xwindows) in the directory ~/abin/afni

Next I should be adding libxp6 but I have failed despite trying all of the following:

I executed the following command: sudo apt-get install libxp6
 and got this response:
libxp6 is already the newest version

>> apt-cache search libxp6
response:
libxp6  - X Printing Extension (Xprint) client library
libxp6-dbg  - X Printing Extension (Xprint) client library (unstripped)

>> afni
response: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory

>> sudo apt-get install libXp.so.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libXp.so.6
E: Couldn't find any package by regex 'libXp.so.6'

Could someone suggest how I can run afni without being stopped by the error message?  Help would be much appreciated.

Thank you.

---

### Post by CarryOn on 2014-10-04
Dear Forum,
I have been able to resolve this issue.    I had been trying to use the wrong version of AFNI for my computer. 
I deleted the linux_gcc32   and chose     linux_openmp_64   instead.
The problem is now resolved.      

Stay calm and .....

---

