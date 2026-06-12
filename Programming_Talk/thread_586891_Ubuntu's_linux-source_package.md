---
title: "Ubuntu's linux-source package"
date: 2007-10-22
forum: Programming Talk
---

### Post by Kow on 2007-10-22
I'm working on upgrading linux-source to 2.6.23.1 (for personal use) and am running into versioning issues. During the module install portion of the process (via debian/rules.d/2-binary-arch.mk) the modules are getting put into debian/linux-image-2.6.23.1-generic/lib/modules/2.6.23-generic while the initrd portion gets setup correctly in debian/linux-image-2.6.23.1-generic/lib/modules/2.6.23.1-generic. I went through all of the scripts and finally just hackishly fixed it by forcing $(KERNELRELEASE) to 2.6.23.1-generic in the kernels makefile. I was wondering if anyone has run into this trouble before? I think the EXTRAVERSION (.1) is being neglected somewhere in the debian packaging rules but I am not seeing it at the moment.

EDIT: Upon further review it is the kernel build settings KERNELRELEASE to 2.6.23-generic. Therefore, it appears likely that the debian scripts are wrong in including the EXTRAVERSION in the /lib/modules/path (they shouldnt be). That, or the kernel build scripts are wrong and should be including EXTRAVERSION. I'm guessing ubuntu kernel dev team will never see this error until they first decide to use a kernel version with an extraversion string added.

---

