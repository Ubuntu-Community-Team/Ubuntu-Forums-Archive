---
title: "Got an error when tried to compile the 2.6.32.2 linux kernel with ubuntu 12.04"
date: 2013-06-07
forum: Packaging and Compiling Programs
---

### Post by cmjauto on 2013-06-07
while I was compiling the 2.6.32.2 linux kernel,I got the error message like this:


In file included from drivers/net/igbvf/ethtool.c:36:0:
drivers/net/igbvf/igbvf.h: At top level:
drivers/net/igbvf/igbvf.h:128:15: error: duplicate member ‘page’
make[3]: *** [drivers/net/igbvf/ethtool.o] Error 1
make[2]: *** [drivers/net/igbvf] Error 2
make[1]: *** [drivers/net] Error 2
make: *** [drivers] Error 2


My version of gcc is 4.6.3 and I am using Ubuntu 12.04 (the kernel I am using is 3.2.0).
I've tried for times but failed, please help!

If this post has gotten into the inappropriate topic category, please tell me where should my post be, thanks. 

Best regards!

---

