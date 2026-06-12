---
title: "How to determine kernel version and patches in Ubuntu?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Joshua66 on 2008-11-01
Hi,
How does one figure out what changes are included in various Ubuntu packages such as linux-image?  I was hoping to find a something like a Changelog for the package, for example.
I looked at:
   [http://packages.ubuntu.com/intrepid/base/linux-image-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/base/linux-image-2.6.27-7-generic)
but couldn't find anything promising.

In this particular case, I'm looking to update from Hardy to Intrepid, but I'd like to know the exact kernel version and set of patches applied to the kernel package in Intrepid.  In particular, I want to know which set of patches regarding the e1000e networking bug are present.  I think a fix was included in Linux 2.6.27.1.

Thanks,
Josh

---

### Post by phidia on 2008-11-01
My intrepid install-which is 64 bit and was up-to-date as of yesterday-I'm not booted in that right now; has the 2.6.26-5 kernel.

I don't know if the x86 version has a later kernel but the release notes might say.

---

### Post by por100pre1 on 2008-11-01
I got the 2.6.27-7-generic kernel in Ubuntu 8.10. The e1000e driver issue has been fixed, check here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

---

