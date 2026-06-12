---
title: "IPv6 support? net/ethernet.h does not have ETHERTYPE_IPV6 defined"
date: 2007-04-24
forum: Programming Talk
---

### Post by mkuutti on 2007-04-24
How am i supposed to identify ipv6 packets when there is no such type available in net/ethernet.h ! In fact, there is no such definition in any file under /usr/include.

Of course I can define 
#define ETHERTYPE_IPV6 0x86dd 
in my code myself, but my opinion is, that it belongs to <net/ethernet.h> where all other types do.

BSD seems to have all ethernet types defined since FreeBSD4, like five years ago. So is my libc6-dev package (where ethernet.h belongs) out-of-date, even though my distribution is Feisty :confused: 

Does anybody know reason why that file is so out-of-date?

---

