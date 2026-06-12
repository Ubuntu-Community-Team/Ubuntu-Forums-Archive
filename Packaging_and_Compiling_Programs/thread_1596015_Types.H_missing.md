---
title: "Types.H missing"
date: 2010-10-13
forum: Packaging and Compiling Programs
---

### Post by montraydavis on 2010-10-13
```

error: sys/types.h: No such file or directory

```I have tried everything from "installing linux headers", to installing "build-essentials", "libc6-dev" and a few others. For some reason, this file is missing as I don't see it in "/usr/include". Any help please?

I'm trying to simply compile a program which uses the types.h header file
There are also a few other headers which seem to be missing as well.!

```

#include <sys/types.h>

```Thanks in advance.

PS: OS= Ubuntu 10.10 LTS

---

### Post by MadCow108 on 2010-10-14
it must be in libc6-dev:
[http://packages.ubuntu.com/maverick/i386/libc6-dev/filelist](http://packages.ubuntu.com/maverick/i386/libc6-dev/filelist)

check again if it is installed. Maybe reinstall it.
create a minimal example and test if that works.
Maybe there is something wrong with the build process.

bttw. there is not ubuntu 10.10 LTS, either 10.10 with has short support or 10.04 which is the long term support version

---

### Post by montraydavis on 2010-10-15
> **MadCow108 said:**
> it must be in libc6-dev:
[http://packages.ubuntu.com/maverick/i386/libc6-dev/filelist](http://packages.ubuntu.com/maverick/i386/libc6-dev/filelist)

check again if it is installed. Maybe reinstall it.
create a minimal example and test if that works.
Maybe there is something wrong with the build process.

bttw. there is not ubuntu 10.10 LTS, either 10.10 with has short support or 10.04 which is the long term support version

Oh great! :) Thanks!!

And what about linux/module.h
 
That seems to also be missing :\

---

