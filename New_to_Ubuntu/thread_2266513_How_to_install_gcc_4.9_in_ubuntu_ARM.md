---
title: "How to install gcc 4.9 in ubuntu ARM ?"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by Jyothi_Krishna_V_S on 2015-02-23
Hi I want to install gcc 4.9 in Ubuntu in ARMv7 multicore processor. The cores are of type Cortex-A7. I tried to add toolchain repository with

sudo add-apt-repository ppa:ubuntu-toolchain-r/test

but failed.

I then tried to make from gcc 4.9.2 branch.  But got the following error.  

In file included from ./bconfig.h:3:0,
                 from ../../gcc-4.9.2/gcc/genmddeps.c:18:
./auto-host.h:2056:16: error: declaration does not declare anything [-fpermissive]
 #define rlim_t long
                ^


Could you help. I prefer precompiled binaries.

---

