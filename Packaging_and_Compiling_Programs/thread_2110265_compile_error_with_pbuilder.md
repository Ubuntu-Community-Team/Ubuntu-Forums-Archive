---
title: "compile error with pbuilder"
date: 2013-01-29
forum: Packaging and Compiling Programs
---

### Post by mwtremblay on 2013-01-29
Hi guys. I am trying my hand at building source packages with pbuilder for Launchpad. The program compiles on my machine without error, but when I try to "pbuilder build *.dsc" I get the following error.

```

configure: exit 1
dh_auto_configure: ./configure --build=x86_64-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/mednafen --disable-maintainer-mode --disable-dependency-tracking returned exit code 1
make: *** [build] Error 25
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

I am not very experienced in deciphering these kinds of error messages so any insight is appreciated. I am on precise.

---

### Post by MadCow108 on 2013-01-31
you have not posted the actual error message, its will be located a few lines earlier

quite often the configure error is not very useful, you want to look at the output of the config.log if it is not helpful (and in usually somewhere in the middle)

to get to that with pbuilder either login and build the package "manually", e.g. via debuild or debian/rules binary
or use a pbuilder hook to drop into the chroot on the build failure
see the pbuilder manpage and an example hook is located in
/usr/share/doc/pbuilder/examples/C10shell

---

### Post by mwtremblay on 2013-01-31
Thank you for the reply. I will try these things and report back. :D

---

### Post by mwtremblay on 2013-02-10
Okay, so I've had some time to return to this and believe I have found the error message in config.log

```

conftest.c:9:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3909: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3934: result: gcc -E
configure:3954: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
configure:3954: $? = 0
configure:3968: gcc -E -D_FORTIFY_SOURCE=2 conftest.c
conftest.c:9:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3968: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>

```

---

### Post by MadCow108 on 2013-02-12
thats one of the intentional errors created by autoconf to throw you off, search for later errors. the last one before it dumps all its variables should be it.

---

### Post by mwtremblay on 2013-02-15
Victory.

Thank you so much for your help. config.log is very easy to understand once you learn how to ignore all of the random messages it spits out.

+1000 internets to you.:D

---

