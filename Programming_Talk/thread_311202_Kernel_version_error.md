---
title: "Kernel version error"
date: 2006-12-02
forum: Programming Talk
---

### Post by nkwai on 2006-12-02
Hi!
I have a problem that I don't understand at all.
I run Ubuntu 6.10, have installed linux-source, and try to run the following command:
 ```
sudo make-kpkg modules-image
```

Then I get this error:
 ```
exec debian/rules  DEBIAN_REVISION=2.6.17-10.33  modules-image 
====== making .config because of Makefile ======

test -f .config || test ! -f .config.save || \
                            cp -pf .config.save .config
test -f .config || test ! -f .config || \
                            cp -pf .config .config
test -f .config || test ! -f ./debian/config || \
                            cp -pf ./debian/config  .config
test -f .config || (echo "*** Need a config file .config" && false)
echo "The UTS Release version in include/linux/version.h"; echo "     \"\" "; echo "does not match current version:"; echo "     \"2.6.17.13-ubuntu1\" "; echo "Please correct this."; exit 2
The UTS Release version in include/linux/version.h
     "" 
does not match current version:
     "2.6.17.13-ubuntu1" 
Please correct this.
make: *** [modules-image] Error 2

```

What I don't understand is where it got the version 2.6.17.13-ubuntu1.
Here is the output of my kernel version:
 ```
nkwai@nkwai-laptop:/$ uname -r
2.6.17-10-386

```
 ```
nkwai@nkwai-laptop:/$ cat /proc/version
Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
```

Can please anyboady tell me what's wrong?
Thank You.

---

