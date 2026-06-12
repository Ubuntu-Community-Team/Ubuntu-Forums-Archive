---
title: "compiling custom kernel - error"
date: 2007-02-20
forum: Packaging and Compiling Programs
---

### Post by nickoli_02 on 2007-02-20
I'm following [this]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2") guide in order to compile my own kernel (version 2.6.20). I downloaded the tar.bz2 archive from [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") and went through the configuration process and such.

I'm stuck on step 6 in the guide where I compile using:

```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

This is the error I get:

```
***lots of other stuff before this***

This is kernel package version 10.049ubuntu5.
/usr/bin/make  EXTRAVERSION=-10-generic-custom-kernel  ARCH=i386 \
                             bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CHK     include/linux/version.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2

```

Any ideas?

---

### Post by hod139 on 2007-02-21
I'm not sure why that article calls that the Ubuntu way, as it is the old way.  Anyways, check out the ubuntu wiki page, it seems to be more up-to-date.
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

### Post by nickoli_02 on 2007-02-21
Thanks, I'll check out that guide. I won't be able to get back to this for awhile now, unfortunately

---

