---
title: "dh_usrlocal: is not a directory"
date: 2011-12-19
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-12-19
Getting this error at the very end of the build process.

12.04 server, updated to the latest everything as of today.

I have gone through the relevant manpages and googled around for similar cases, but am at a loss as to what to do to resolve this error. This is my first packaging attempt, so I suspect that I am simply ignorant of something that is common-sense to packaging veterans but not explicit in the documentation.  

```
dh_usrlocal: debian/nslink-tools/usr/local/man/man5/nslink.conf.5 is not a directory
rmdir: failed to remove `debian/nslink-tools/usr/local/man/man5': Directory not empty
dh_usrlocal: rmdir debian/nslink-tools/usr/local/man/man5 returned exit code 1
```

---

### Post by djsephiroth on 2011-12-19
Looks like I need to use dh_installman.

---

