---
title: "Repository Packaging Problems"
date: 2008-10-13
forum: Packaging and Compiling Programs
---

### Post by Patrick793 on 2008-10-13
I am trying to package LMMS for repositories I am making, and the version I am compiling is version 0.4.0, which uses cmake. I have gotten close to finishing getting it ready, but after I run sudo pbuilder build lmms_0.4.0rc2-1ubuntu1.dsc --pbuilderroot I get this:

```
Install the project...
-- Install configuration: "relwithdebinfo"
-- Installing /usr/bin/lmms
CMake Error: Error in cmake code at
/tmp/buildd/lmms-0.4.0rc2/cmake_install.cmake:35:
FILE INSTALL cannot copy file "/tmp/buildd/lmms-0.4.0rc2/CMakeFiles/CMakeRelink.dir/lmms" to "/usr/bin/lmms".
Current CMake stack: 
[1]	/tmp/buildd/lmms-0.4.0rc2/cmake_install.cmake
make[1]: *** [install] Error 255
make[1]: Leaving directory `/tmp/buildd/lmms-0.4.0rc2'
make: *** [install] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc/sys/fs/binfmt_misc filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//25633 and its subdirectories

```

Can anyone help?

---

### Post by bapoumba on 2008-10-14
Moved to "Packaging and Compiling Programs".

---

### Post by InfinityCircuit on 2008-10-14
The package is trying to install into /usr/bin/whatever.  It should try to install to debian/{packagename}/usr/bin/whatever instead.  It's hard to give an exact way to fix this problem without more information--like debian/rules.

---

