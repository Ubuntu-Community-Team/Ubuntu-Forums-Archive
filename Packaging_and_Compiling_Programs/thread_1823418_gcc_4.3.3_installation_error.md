---
title: "gcc 4.3.3 installation error"
date: 2011-08-12
forum: Packaging and Compiling Programs
---

### Post by ravish112 on 2011-08-12
Hi,
 
I am trying to compile gcc 4.3.3 on ubuntu 11.04 machine. After installation It did not created any libraries under lib64 folder, where this is an x86_64 bit machine.
 
The config parameter which I gave was
 
./configure --prefix=/myfolder/gnu/gcc/4.3.3/ --disable-multilib --enable-shared --with-ld=/usr/bin/ld.
 
After Installation I went and saw the installation directory structure, it was like this:-
 
bin
include
lib
libexec
 
How ever for 64 bit machine the lib64 folder should be created. Where as it got created on ub1010-x86_64 machine.
 
Could you please provide a solution for above issue. Is there any config parameter is missing or installation is not proper.
 
Thanks,

---

### Post by MadCow108 on 2011-08-13
you can usually set the library directory with the --libdir flag

but under debian and ubuntu systems lib64 is usually just a symlink to lib (the lib64 in the FHS was a mistake and is likely to be rectified in the next revision to support proper debian-esque multi-arch paths).
why do you need a lib64 directory if you are using a custom prefix anyway?

---

