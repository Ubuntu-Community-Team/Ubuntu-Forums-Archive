---
title: "No static/dynamic library files are installed for google test on 12.04"
date: 2012-06-03
forum: Programming Talk
---

### Post by eddyxu on 2012-06-03
After upgrading 11.10 to 12.04, my source code that relies google-test to do the unittest is failed to  compile. 

It seems the header files are appropriately installed, but the library files are missing from /usr/lib?

Is it a bug?

---

### Post by MadCow108 on 2012-06-03
its no bug, according to upstream you should compile it yourself
see the package changelog

> gtest (1.6.0-1) unstable; urgency=low
  
  Use of precompiled libgtest is no longer recommended.  See README.Debian
  for instructions on using gtest with your projects.  The precompiled
  shared library has been removed and the static library will be removed
  in a future upload.
  
  The script gtest-config is no longer supplied since upstream's
  autoconfigure-based build is deprecated.

---

