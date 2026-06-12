---
title: "Kernel AODV v2.2.2 - make error"
date: 2007-10-28
forum: Programming Talk
---

### Post by goforce on 2007-10-28
Hi all,

I tried to do a Make on the Kernel AODV source codes version 2.2.2, the target=arm but it gives the following errors even though I have change nothing in the codes. 

For your information, I'm running Ubuntu 7.10 with the latest Linux kernel version 2.6.22. I trace the error and can't find struct type defined as "nf_hook_ops" in usr/include/linux/netfilter.h

Am I missing something here? why is the netfilter.h different from this [http://lxr.linux.no/source/include/linux/netfilter.h](http://lxr.linux.no/source/include/linux/netfilter.h) ??? It should be the latest version on my system.

Thanks alot for your help.

---------------------------------------------------------------------------------------------------------
**Make error:**

arm-linux-gcc -O3 -DMODULE -D__KERNEL__ -DLINUX -DARM -DMESSAGES -DAODV_GATEWAY -DAODV_SIGNAL -I/home/adhoc/ipaq/include/ -c module.c -o module.o
In file included from aodv_route.h:17,
                 from packet_in.h:21,
                 from module.h:20,
                 from module.c:9:
packet_queue.h:78: warning: `struct nf_info' declared inside parameter list
packet_queue.h:78: warning: its scope is only this definition or declaration, which is probably not what you want
module.c: In function `init_module':
module.c:89: invalid use of undefined type `struct nf_hook_ops'
module.c:90: invalid use of undefined type `struct nf_hook_ops'
module.c:91: invalid use of undefined type `struct nf_hook_ops'
module.c:92: invalid use of undefined type `struct nf_hook_ops'
module.c :93: invalid use of undefined type `struct nf_hook_ops'
module.c:96: invalid use of undefined type `struct nf_hook_ops'
module.c:97: invalid use of undefined type `struct nf_hook_ops'
module.c:98: invalid use of undefined type `struct nf_hook_ops'
module.c:99: invalid use of undefined type `struct nf_hook_ops'
module.c:100: invalid use of undefined type `struct nf_hook_ops'
module.c: At top level:
module.c:11: storage size of `input_filter' isn't known
module.c:12: storage size of `output_filter' isn't known
make: *** [module.o] Error 1
---------------------------------------------------------------------------------------------------------

---

