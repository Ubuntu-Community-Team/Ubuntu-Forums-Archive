---
title: "lib not found"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by hotrodwinston on 2008-05-20
while trying to compile the rt73 drivers from serialmonkey i got this error "not found: ./lib/modules/2.6.15-26-386/build/ :no such file or directory" what do i need to do?

---

### Post by dwhitney67 on 2008-05-20
Please verify which version of the Linux Kernel you are running.  You can do so by running this command:
```
$ uname -r
```

If the output you get shows a version number that differs from the statement you provided earlier (./lib/modules/[COLOR="Blue"]2.6.15-26-386[/COLOR]/build/), then herein lies your problem.

You may need to edit whatever statements, Makefiles, or run ./configure in the directory where you are attempting to build to ensure that the version numbers match.

If the version numbers match, then perhaps your system is lacking the kernel source code.  I believe to get that:
```
$ sudo apt-get install kernel-devel
```

---

