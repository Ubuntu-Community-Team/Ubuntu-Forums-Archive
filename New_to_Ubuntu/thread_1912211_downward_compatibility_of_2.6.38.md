---
title: "downward compatibility of 2.6.38"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by maulikprabhudesai on 2012-01-20
I am trying to install PerfInspector on my Ubuntu 11.04 2.6.38
The problem is the software was last tested in a 2.6.32 kernel where it worked perfectly fine. while installing it on my kernel I get errors like ioctl call not recognised and functions like init_MUTEX not defined
I figured it is because the support for them has been removed from 2.6.38 and so used compat_ioctl and sema_init in their place
but then the driver installation throws me errors with a lot of other functions

is there any way I can make my version of kernel downward compatible with 2.6.32?

also is there any problem with the 2.6.32 header installation? I tried to install it so that my software could work but I had a problem with the installation of linux-headers 

hoping for your reply

---

