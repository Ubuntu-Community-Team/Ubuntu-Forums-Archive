---
title: "Unable to find nf_register_hook function in netfilter.c"
date: 2007-11-29
forum: Programming Talk
---

### Post by niaf on 2007-11-29
Hello,

I work on Ubuntu 7.10 and I'm investigating the netfilter source code.  
I have downloaded the linux source using apt-get source linux-source-2.6.22

I'm looking for the nf_register_hook function which is declared in:
/usr/src/linux-headers-2.6.22-14/include/linux/netfilter.h or
/usr/src/linux-headers-2.6.22-14-generic/include/linux/netfilter.h

The problem is that I can't find the implementation of this function in linux-source-2.6.22-2.6.22/net/ipv4/netfilter.c

How is that possible? Can somebody please help?

---

### Post by niaf on 2007-11-30
Finally I found the implementation of the nf_register_hook function it was in linux-source-2.6.22-2.6.22/net/netfilter/core.c.  

But why in this file and not in a file named netfilter.c, I don't see the relationship between the file netfilter.h and core.c...

---

