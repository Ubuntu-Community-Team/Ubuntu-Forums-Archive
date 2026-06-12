---
title: "Kernel make deb-pkg puts higher versions on the deb names than the sources are"
date: 2014-01-22
forum: Packaging and Compiling Programs
---

### Post by User4519 on 2014-01-22
Hi :)

I'm patching the 3.11.0 kernel sources with SCST and creating deb packages using make deb-pkg. It's working fine, except one thing is really puzzling me.

Here's a dpkg list of kernel related packages:
```
ii  linux-firmware-image                3.11.0-15-scst                             amd64        Linux kernel firmware, version 3.11.10ii  linux-headers-3.11.0-15             3.11.0-15.23                               all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic     3.11.0-15.23                               amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
ii  linux-headers-3.11.10               3.11.0-15-scst                             amd64        Linux kernel headers for 3.11.10 on amd64
ii  linux-headers-generic               3.11.0.15.16                               amd64        Generic Linux kernel headers
ii  linux-image-3.11.0-15-generic       3.11.0-15.23                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.10                 3.11.0-15-scst                             amd64        Linux kernel, version 3.11.10
ii  linux-image-extra-3.11.0-15-generic 3.11.0-15.23                               amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.11.0.15.16                               amd64        Generic Linux kernel image
ii  linux-libc-dev                      3.11.0-15-scst                             amd64        Linux support headers for userspace development
ii  linux-source-3.11.0                 3.11.0-15.23                               all          Linux kernel source for version 3.11.0 with Ubuntu patches
```

Which corresponds with the fact that **[FONT=courier new]make -j8 KDEB_PKGVERSION="3.11.0-25-scst" deb-pkg[/FONT]** results in:
```
dpkg-deb: building package `linux-firmware-image' in `../linux-firmware-image_3.11.0-25-scst_amd64.deb'.dpkg-deb: building package `linux-headers-3.11.10' in `../linux-headers-3.11.10_3.11.0-25-scst_amd64.deb'.
dpkg-deb: building package `linux-libc-dev' in `../linux-libc-dev_3.11.0-25-scst_amd64.deb'.
dpkg-deb: building package `linux-image-3.11.10' in `../linux-image-3.11.10_3.11.0-25-scst_amd64.deb'.
```

What's puzzling me is that I'm building the 3.11.0 sources, using the .configure file from the running 3.11.0-25-generic kernel. Yet, **[FONT=courier new]make deb-pkg[/FONT]** names the **[FONT=courier new]-image[/FONT]** and **[FONT=courier new]-headers[/FONT]** packages as version 3.11.10... What gives? What am I doing wrong?

TIA :)

Daniel

EDIT: Dove into the builddeb script and figured out what environment variable I should set to specify my own version. It's [FONT=courier new]**KERNELRELEASE**[/FONT], so in my specific case, I can do something like:
```
KERNELREV=3.11.0-15; make -j8 KERNELRELEASE="$KERNELREV-scst" KDEB_PKGVERSION="$KERNELREV-scst" deb-pkg
```
or, if scripted to use the currently (running) kernel's revision (minus "-generic" or similar suffix):
```
KERNELREV=$(uname -r|sed 's:[^0-9]*$::'); make -j8 KERNELRELEASE="$KERNELREV-scst" KDEB_PKGVERSION="$KERNELREV-scst" deb-pkg
```

---

