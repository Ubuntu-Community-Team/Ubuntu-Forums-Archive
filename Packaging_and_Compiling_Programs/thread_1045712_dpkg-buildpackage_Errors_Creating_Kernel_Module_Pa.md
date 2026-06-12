---
title: "dpkg-buildpackage: Errors Creating Kernel Module Package"
date: 2009-01-20
forum: Packaging and Compiling Programs
---

### Post by jhwilliams on 2009-01-20
Hello,

I wrote a module switch script that seems to have been useful and now am trying to build a debian/ubuntu package from the Realtek r8168 driver source tarball to increase the utility and ease of administration for the workaround. (Point: deb packages are better than shell scripts.)

When I try:
```
tar r8168-8.010.00.tar.bz2 
cd r8168-8.010.00
dh_make -e jameson@jamesonwilliams.com -f ../r8168-8.010.00.tar.bz2
dpkg-buildpackage -rfakeroot
```

dpkg-buildpackage fails:
```
make[2]: Entering directory `/home/jameson/r8168-8.010.00/src'
/usr/bin/make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/src modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
mkdir: cannot create directory `/src': Permission denied
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[4]: *** No rule to make target `/src/Makefile'.  Stop.
```

SUBDIRS=/src is in the make action for the modules target in the tarball's ./src/Makefile :42. As you can see, the result is that the kernel header Makefiles are incorrectly referenced. I tried changing and omitting this variable, but to no avail.

What should I do?

Thank you!
Jameson

---

