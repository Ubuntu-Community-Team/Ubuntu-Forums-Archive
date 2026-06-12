---
title: "howto pass -m32 option to ld command?"
date: 2010-02-15
forum: Packaging and Compiling Programs
---

### Post by jamaas on 2010-02-15
Hi Guys,

Noob here, attempting to get a programme to compile on a 64 bit system, has worked fine on 32.  I found a 'Makedefs' file and added the -m32 option to the CFLAGS and LFLAGS as such.  This eliminated pages of compiling errors however I still get the one below.  I've googled and found some reference to a requirement to pass the -m32 option to the ld command as well.  Could anyone tell me how and where to do this, i.e. add the -m32 command to the ld command?   There are other commands in this Makedefs file ... it could be one of them?

Thanks

Jim

CFLAGS = -m32 -fPIC -c -I $(AX_WORKING_FOLDER) -o $@ $<
LFLAGS = -m32 -fPIC -shared -Wl,-E -o $@ $< $(AX_WORKING_FOLDER)/libacsl.a -lstdc++
#CFLAGS = -fPIC -c -I $(AX_WORKING_FOLDER) -o $@ $<
#LFLAGS = -fPIC -shared -Wl,-E -o $@ $< $(AX_WORKING_FOLDER)/libacsl.a -lstdc++



--------------------------
/Chicken$ make
gcc -m32 -fPIC -shared -Wl,-E -o chickgrowv1.so chickgrowv1.o /opt/acslX/libacsl.a -lstdc++
/usr/bin/ld: i386:x86-64 architecture of input file `chickgrowv1.o' is incompatible with i386 output
chickgrowv1.o: In function `zzderivative(unsigned long, unsigned long)':
chickgrowv1.cpp:(.text+0x1e541): undefined reference to `pow'
chickgrowv1.cpp:(.text+0x1e59f): undefined reference to `pow'
chickgrowv1.cpp:(.text+0x1e7c1): undefined reference to `pow'
chickgrowv1.cpp:(.text+0x1e8d0): undefined reference to `pow'
/usr/bin/ld: final link failed: Invalid operation
collect2: ld returned 1 exit status
make: *** [chickgrowv1.so] Error 1

---

### Post by l0xin on 2010-02-15
"LDFLAGS" should be what you're looking for.

---

### Post by Zugzwang on 2010-02-16
First of all, delete all your "old" ".o" files. The error message is basically telling you that you that "chickgrowv1.o" has not been compiled in 32-bit mode. Then, install the 32-bit libraries for your 64-bit system by installing the "g++-multilib" package.

---

### Post by jamaas on 2010-02-17
Thanks, yes did not realise at first that old .o file was hanging around.  Then changes in Makedef file seemed to work ok.  

Appreciate the help.

Jim

---

