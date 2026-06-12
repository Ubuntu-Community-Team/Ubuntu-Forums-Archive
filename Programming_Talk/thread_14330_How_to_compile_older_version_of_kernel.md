---
title: "How to compile older version of kernel?"
date: 2005-02-06
forum: Programming Talk
---

### Post by isaac on 2005-02-06
Can some one teach me how to compile order version kernel (linux-2.4.20) because i needed it to make my webcam driver to work.. there's also some problem here which make me unable to complete it step by step because kernel linux-2.4.20 need gcc version 2.95.3 but the default version for ubuntu is gcc-3.3.4 and i have tried to install the gcc -version 2.95.3 but failed with some error at the point below (when i run make with root:

make[2]: Entering directory `/home/isaac/gcc-2.95.3/gcc/ch'
gcc -c  -DIN_GCC   -g -O2     -I. -I.. -I. -I./.. -I./../config -I./../../include loop.c
loop.c:321:8: missing terminating " character
loop.c:322:38: missing terminating " character
make[2]: *** [loop.o] Error 1
make[2]: Leaving directory `/home/isaac/gcc-2.95.3/gcc/ch'
make[1]: *** [cc1chill] Error 2
make[1]: Leaving directory `/home/isaac/gcc-2.95.3/gcc'
make: *** [all-gcc] Error 2


can some one help me what's really my problem is? 

Oh i still have one question left? is video for linux modules preinstalled in the default kernel for ubuntu?

---

