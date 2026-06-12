---
title: "New error?"
date: 2005-04-22
forum: Packaging and Compiling Programs
---

### Post by zolookas on 2005-04-22
```
root@super:/usr/src/linux-2.6.11.7 # make menuconfig
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:305:24: asm/socket.h: No such file or directory
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2
root@super:/usr/src/linux-2.6.11.7 #
``` 
Strange, i never had this error before...

---

