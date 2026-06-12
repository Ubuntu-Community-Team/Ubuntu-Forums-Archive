---
title: "Compiling glibc on Ubuntu 18.04"
date: 2020-09-19
forum: Packaging and Compiling Programs
---

### Post by rafimoor on 2020-09-19
I am trying to compile glibc on Ubuntu 18.04. I tried:

apt build-dep glibc
apt source glibc
cd glibc-2.27
debuild -b -uc -us

The build failed with 9 tests failures.

I've found out that there is a version 2.27-3ubuntu1.3 which is newer then what was downloaded with "apt source".
apt source glibc=2.27-3ubuntu1.3 didn't work, so I've downloaded and opened it manually.
This reduced the failures to 6. Here is the end of the log:

+---------------------------------------------------------------------+
|     Encountered regressions that don't match expected failures.     |
+---------------------------------------------------------------------+
FAIL: nptl/test-condattr-printers
FAIL: nptl/test-cond-printers
FAIL: nptl/test-mutexattr-printers
FAIL: nptl/test-mutex-printers
FAIL: nptl/test-rwlockattr-printers
FAIL: nptl/test-rwlock-printers
debian/rules.d/build.mk:115: recipe for target '/pkgsrc/debian/glibc-2.27/stamp-dir/check_libc' failed
make: *** [/pkgsrc/debian/glibc-2.27/stamp-dir/check_libc] Error 1
dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
debuild: fatal error at line 1152:
dpkg-buildpackage -rfakeroot -us -uc -ui -b failed

What could be the problem?

Thanks

---

### Post by rafimoor on 2020-09-29
Well, after some work I've found a solution/workaround, and (again) I answer myself ;)

Edit the file [FONT="Calibri"][COLOR=#000000]sysdeps/unix/sysv/linux/test-errno-linux.c[/COLOR][/FONT] and replace the line:

                      quotactl, Q_GETINFO, NULL, -1, (caddr_t) &dqblk); 
with:
                      quotactl, QCMD(Q_GETINFO,USRQUOTA), NULL, -1, (caddr_t) &dqblk); 

Integrate the change in the build source:

dpkg-source --commit

Rename /usr/bin/gdb to something else for the time of compilation.

Build the package

---

