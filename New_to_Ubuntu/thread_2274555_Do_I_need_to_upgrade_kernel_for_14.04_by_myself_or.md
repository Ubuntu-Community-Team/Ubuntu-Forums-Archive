---
title: "Do I need to upgrade kernel for 14.04 by myself or is it rather not a good thing todo"
date: 2015-04-20
forum: New to Ubuntu
---

### Post by sebastiaan5 on 2015-04-20
I'm wondering if it's good/necessary to upgrade the kernel by yourself or does it go automatically with updates?

running 3.16.0-34-generic at the moment.

greetings

---

### Post by craig10x on 2015-04-20
If you mean the normal updates to the 3.16 kernel then the answer would be it goes automatically with updates....you will get them in the software updater as ubuntu sends them down...

---

### Post by sebastiaan5 on 2015-04-20
I mean upgrading to 3.18

---

### Post by deadflowr on 2015-04-20
You'd need to install manually.
At least Ubuntu's Kernel team build kernel packages, so it is relatively easy to do.
No compiling required.

Looky here on how to do so
[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Upstream_kernels_archive](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Upstream_kernels_archive)

---

### Post by grahammechanical on 2015-04-20
If you are using Ubuntu 14.04 and you have the 3.16 kernel, then you have the kernel that Ubuntu 14.10 had when it was released. Ubuntu 15.04 will be released in a few days time and it comes with the 3.19 kernel.

I would not recommend kernel 3.18 as it was quickly replaced by kernel 3.19 during the 26 week development period of Ubuntu 15.04. Is there any reason why you want to install a newer kernel? Keep in mind the kernel 3.19 has not been tested with Ubuntu 14.04.

You actually have 14.04.2 and in August this year 14.04.3 will be released and it will have not only the 3.19 kernel that Ubuntu 15.04 has but also the rest of the hardware enablement stack and it will have been tested with the 14.04 code base.

Regards.

---

### Post by wildmanne39 on 2015-04-20
There is not a good reason to install a new kernel unless you have new hardware that is supported in the new kernel and not the old one or you are having issues like with video card or wireless that can be resolved by upgrading.

---

### Post by sebastiaan5 on 2015-04-21
ok :) thank you all for this awesome feedback :)

greetings

---

