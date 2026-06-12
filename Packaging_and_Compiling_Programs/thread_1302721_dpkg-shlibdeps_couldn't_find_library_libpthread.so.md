---
title: "dpkg-shlibdeps couldn't find library libpthread.so.0"
date: 2009-10-27
forum: Packaging and Compiling Programs
---

### Post by shankao asd on 2009-10-27
Hi, I'm trying to create a new package but dh_shlibdeps gives me an error about a library it cannot find:

```
dpkg-shlibdeps: error: couldn't find library libpthread.so.0 needed by debian/opensimulator/usr/lib/opensimulator/libode-x86_64.so (ELF format: 'elf64-x86-64'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-arch] Error 1
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

...but dpkg can find that library without problems...

```
shankao@clotilde:~/dev/opensimulator-0.6.6.1$ dpkg -S libpthread.so.0
libc6-i686: /lib/tls/i686/cmov/libpthread.so.0
libc6: /lib/libpthread.so.0
shankao@clotilde:~/dev/opensimulator-0.6.6.1$
```

I suppose the library should be found automaticaly, but if not, how can I tell dh_shlibdeps where it is located?

The note in the error message about not searching in binary packages that do not have any shlibs or symbols file can be a hint, but as libpthread seems somehow included in libc6, it has not any of those shlibs or symbols file for its own...

Any help would be appreciated :)

---

### Post by kenrandrews on 2010-04-06
Did you ever find a solution for this, I have the same problem.

---

### Post by Zoot7 on 2010-04-08
I'd wager you'd need one of the following:

```
mark@mark-xps:~$ apt-file search libpthread.so.0
libc6: /lib/libpthread.so.0
libc6-amd64: /lib64/libpthread.so.0
libc6-i686: /lib/i686/cmov/libpthread.so.0
libc6-xen: /lib/i686/nosegneg/libpthread.so.0
```

---

