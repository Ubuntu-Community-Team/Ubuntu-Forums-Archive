---
title: "Can't find version.h"
date: 2013-06-17
forum: Packaging and Compiling Programs
---

### Post by kr651129 on 2013-06-17
I'm trying to compile v4l-dvb and I've installed linux-source and kernel-headers, rebooted and I'm still getting this message:

```
In file included from <command-line>:0:0:
/home/k/src/v4l-dvb-3724e93f7af5/v4l/config-compat.h:1245:1: fatal error: include/linux/version.h: No such file or directory
compilation terminated.
```

Thoughts?

Thanks!

---

### Post by markbl on 2013-06-18
You need to install linux-libc-dev package.

FYI, not sure how others work this out but I use apt-file:
```

mark@pc:~ apt-file search include/linux/version.h
linux-libc-dev: /usr/include/linux/version.h
linux-libc-dev-arm64-cross: /usr/aarch64-linux-gnu/include/linux/version.h
linux-libc-dev-armel-cross: /usr/arm-linux-gnueabi/include/linux/version.h
linux-libc-dev-armhf-cross: /usr/arm-linux-gnueabihf/include/linux/version.h
linux-libc-dev-powerpc-cross: /usr/powerpc-linux-gnu/include/linux/version.h

```

---

### Post by oldos2er on 2013-06-18
Moved to Packaging & Compiling Programs.

---

### Post by kr651129 on 2013-06-18
> **markbl said:**
> You need to install linux-libc-dev package.

FYI, not sure how others work this out but I use apt-file:
```

mark@pc:~ apt-file search include/linux/version.h
linux-libc-dev: /usr/include/linux/version.h
linux-libc-dev-arm64-cross: /usr/aarch64-linux-gnu/include/linux/version.h
linux-libc-dev-armel-cross: /usr/arm-linux-gnueabi/include/linux/version.h
linux-libc-dev-armhf-cross: /usr/arm-linux-gnueabihf/include/linux/version.h
linux-libc-dev-powerpc-cross: /usr/powerpc-linux-gnu/include/linux/version.h

```

Thanks for the info!  I've installed that package as recommend and I'm still getting the same error.

---

