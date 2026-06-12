---
title: "Unable to link shared libraries not under the system library directories on Ubuntu 12"
date: 2014-02-04
forum: Programming Talk
---

### Post by Sung_Am_YANG on 2014-02-04
I created a shared library, libsslab_core.so.1.0.0 using gcc with proper options. I am pretty sure that the shared library works because I already linked it to another source code (I explicitly tells a compiler, gcc, the location of the library using -l option of the compiler).

After testing the library works, I tried to integrate the library into my Linux machine. I went to the /etc/ld.so.conf.d/ and added a file, sslab.conf. In the file I just typed the absolute path of the library, /opt/lib/sslab. Next, I executed ldconfig as a root to update the cache file of ldconfig. And I checked if the system finds the newly added library by typing ldconfig -p | grep libsslab. My Linux machine found the library, so I thought everything is finished.

However, when I try to compile a source code using the library, it gives me the following error:

/usr/bin/ld: cannot find -lsslab_core

When I move the library to /usr/local/lib, update the content of sslab.conf, and execute ldconfig as a root. I can use the shared library without any problems.

Do you have any ideas about the problem that I've come across on Ubuntu 12.04?

For your information, I refer to a document in TLDP to generate my own shared library. Here is the link: [http://www.tldp.org/HOWTO/Program-Library-HOWTO/](http://www.tldp.org/HOWTO/Program-Library-HOWTO/)

P.S. I already posted this question on stackoverflow, but I haven't solved the problem yet. Here is the link: [http://stackoverflow.com/questions/21541786/unable-to-link-shared-libraries-not-under-the-system-library-directories-on-ubun](http://stackoverflow.com/questions/21541786/unable-to-link-shared-libraries-not-under-the-system-library-directories-on-ubun)

---

### Post by steeldriver on 2014-02-04
Hello and welcome to the forums

This is not my area of expertise but I think what you're bumping up against here is that ldconfig (and ldd itself) controls the search path for library linkage at *runtime *- the compiler still searches for shared libraries at build time in the order shown by

```
gcc --print-search-dirs | grep ^libraries
```

plus any explicit paths that you give using the -L directive e.g.

```
-L /opt/lib/sslab -lsslab_core
```

---

### Post by abbas2 on 2014-02-06
Hi, 
I am trying to make a program in mu ubuntu 13.10 , but it gives me following error:
"error: #error This file requires compiler and library support for the ISO C++ 2011 standard. This support is currently experimental, and must be enabled with the -std=c++11 or -std=gnu++11 compiler options."
how can i solve this problem?

---

