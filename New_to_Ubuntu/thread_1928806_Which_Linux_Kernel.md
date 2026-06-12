---
title: "Which Linux Kernel ?"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by cat2005 on 2012-02-20
I am using Ubuntu 10.10 in a dual boot with Win7.  

I want to keep 10.10 but update the kernel.  However, my update manager shows so many kernel options.  Which do I select?  How do I know the difference among them?  Is one better than another?  

I don't do anything fancy.  I just do typical desktop stuff.  I currently have 2.6.35-28. kernel.

I appreciate your input.  

Here are the choices:

#1 
Complete Generic Linux Kernel
linux-generic-pae (size:  5 kb)

#2
Header files related to Linux kernel version 2.6.35
linux-headers-2.6.35-32 (new install) (size 10 mb)

#3
Linux kernel headers for version 2.6.35 on x86
linux-headers-2.6.35-32-generic-pae (new install) (size 808 kb)

#4
Generic Linux kernel headers
linux-headers-generic-pae (size 5 kb)

#5
Linux kernel image for version 2.6.35 on x86
linux-image-2.6.35-32-generic-pae (new install) (size 32 mb)

#6
Generic Linux kernel image
linux-image-generic-pae (size 5 kb)

#7
Linux kernel headers for development
linux-libc-dev (size 834 kb)

---

### Post by 3rdalbum on 2012-02-20
The packages that include the word "headers" aren't actually kernels, they are the development headers of the associated kernel. The development headers are useful if you need to compile a driver from source.

If you install the "linux-generic-pae" package and update it when prompted, you will always have the latest Linux PAE kernel. This package always installs the latest Linux PAE kernel whenever installed or updated.

---

### Post by cat2005 on 2012-02-21
> **3rdalbum said:**
> The packages that include the word "headers" aren't actually kernels, they are the development headers of the associated kernel. The development headers are useful if you need to compile a driver from source.

If you install the "linux-generic-pae" package and update it when prompted, you will always have the latest Linux PAE kernel. This package always installs the latest Linux PAE kernel whenever installed or updated.


3rdalbum,

2 questions:

a)  Should I select #1 from the list of choices?  It is the only option I see listing "linux-generic-pae".  However, it is only 5 kb in size.  Is that really all I need?

b)  Does that mean I will be able to boot with both kernels (i.e, my current and then this new one)?  I want the new kernel to replace the old kernel.  Will this update replace the old kernel with the new one?  Or will it leave the old kernel intact?

Thanks!

---

### Post by matt_symes on 2012-02-21
> **cat2005 said:**
> 3rdalbum,

2 questions:

a)  Should I select #1 from the list of choices?  It is the only option I see listing "linux-generic-pae".  However, it is only 5 kb in size.  Is that really all I need?


It's a meta package that will install the latest kernel when it comes out. It depends on the latest kernel so when it gets updated it will download the latest kernel and install that as well.

```
matthew@matthew-Aspire-7540:~$ apt-cache show linux-generic-pae
Package: linux-generic-pae
Priority: optional
Section: **metapackages**
Installed-Size: 30
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.17.17
Depends: **linux-image-generic-pae** (= 3.2.0.17.17)
Filename: pool/main/l/linux-meta/linux-generic-pae_3.2.0.17.17_i386.deb
Size: 1716
MD5sum: 63eeba505707a587645c0b23d6ea9324
SHA1: 5e7952ee11d06948b2b957a34e4ee3f18c044a30
SHA256: 5e705d406f4c07c3d3d801785b851e7704354514a57a378246d774550e227f92
Description-en: Complete Generic Linux kernel
 [B]This package will always depend on the latest complete generic Linux kernel
 available.[/B]
Description-md5: 5d722da329763b9342d322f5a140005c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
matthew@matthew-Aspire-7540:~$
```
> 
b)  Does that mean I will be able to boot with both kernels (i.e, my current and then this new one)?  I want the new kernel to replace the old kernel.  Will this update replace the old kernel with the new one?  Or will it leave the old kernel intact?

Thanks!

It's not a kernel but a package that will install the latest kernel. The newly installed kernel will be available from the GRUB menu when the system starts up. The old kernel will also be in the GRUB menu until you uninstall it.

It's good advice to keep at least 2 kernels on your system in case there are problems with the newest kernel. You can then boot into the old kernel.

Kind regards

---

### Post by cat2005 on 2012-02-23
> **matt_symes said:**
> It's a meta package that will install the latest kernel when it comes out. It depends on the latest kernel so when it gets updated it will download the latest kernel and install that as well.

```
matthew@matthew-Aspire-7540:~$ apt-cache show linux-generic-pae
Package: linux-generic-pae
Priority: optional
Section: **metapackages**
Installed-Size: 30
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.17.17
Depends: **linux-image-generic-pae** (= 3.2.0.17.17)
Filename: pool/main/l/linux-meta/linux-generic-pae_3.2.0.17.17_i386.deb
Size: 1716
MD5sum: 63eeba505707a587645c0b23d6ea9324
SHA1: 5e7952ee11d06948b2b957a34e4ee3f18c044a30
SHA256: 5e705d406f4c07c3d3d801785b851e7704354514a57a378246d774550e227f92
Description-en: Complete Generic Linux kernel
 [B]This package will always depend on the latest complete generic Linux kernel
 available.[/B]
Description-md5: 5d722da329763b9342d322f5a140005c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
matthew@matthew-Aspire-7540:~$
```
It's not a kernel but a package that will install the latest kernel. The newly installed kernel will be available from the GRUB menu when the system starts up. The old kernel will also be in the GRUB menu until you uninstall it.

It's good advice to keep at least 2 kernels on your system in case there are problems with the newest kernel. You can then boot into the old kernel.

Kind regards


I understand now.  Thanks!

---

