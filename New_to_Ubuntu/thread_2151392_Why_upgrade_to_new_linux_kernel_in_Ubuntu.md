---
title: "Why upgrade to new linux kernel in Ubuntu?"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by duttashantanu on 2013-06-04
I want to know what is the benefit/necessity of upgrading to a new kernel?

---

### Post by prodigy_ on 2013-06-04
New revisions of the the same kernel contain bugfixes and are considered more stable and secure (though regressions also happen sometimes). New kernel releases contain new device drivers and various other improvements but are also more likely to break things since new always equals relatively untested.

So you can always upgrade (and then go back to a previous version in case of any issues).

---

### Post by grahammechanical on 2013-06-04
If all your hardware works as it should then there is little benefit of upgrading to a new kernel but the existing kernel might be modified to bring in some bug fixes. Linux needs to keep up with the latest hardware. So, the kernel is under constant development. And there is a need to keep track of the changes made to the code in case the changes break things. So, kernels are numbered. And that makes it seem to us that there are new kernels. So, each version of Ubuntu as it is released has the latest stable kernel at that time. 

Ubuntu 12.04 has kernel 3.2.0. Ubuntu 12.10 has kernel 3.5.0. Ubuntu 13.04 has kernel 3.8.0. And Ubuntu 13.10 will have kernel 3.9.0 or 3.10.0. Those running 12.04 do not need to install kernel 3.9.0. Some people like to install the latest but most users do not need to change except as part of a normal update.

Regards.

---

