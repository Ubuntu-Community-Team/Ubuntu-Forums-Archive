---
title: "Creating new .deb: chromeless"
date: 2012-05-26
forum: Packaging and Compiling Programs
---

### Post by Simonpatp on 2012-05-26
I am attempting to create a .deb package, but have run into some issues.
I get the following error
```
 dpkg-genchanges  >../chromeless_0.3-12-1_amd64.changes
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2

```

previously, before I moved the extraction process away, i got this error:```
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.
   dh_testroot
ERROR: ld.so: object 'libfakeroot-sysv.so' from LD_PRELOAD cannot be preloaded: ignored.

```


I am building with the command
$ debuild -us -uc

What is the issue? building debs seems to be excessivly difficult.

also, is there a way to ignore a file (tar.gz) that it downloads without moving it to /tmp?

all files are attached

---

