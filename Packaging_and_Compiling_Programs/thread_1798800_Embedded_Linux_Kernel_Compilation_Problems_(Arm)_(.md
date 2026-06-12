---
title: "Embedded Linux Kernel Compilation Problems (Arm) (Qwerk Board)"
date: 2011-07-06
forum: Packaging and Compiling Programs
---

### Post by shiman6 on 2011-07-06
I am starting a custom embedded linux for the qwerk board, using modified TeRK source code, and i keep getting this error:

```

make[1]: Entering directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src'
make -C IceE-1.0.0 all
make[2]: Entering directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0'
making all in src
make[3]: Entering directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0/src'
making all in IceE
make[4]: Entering directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0/src/IceE'
arm-linux-g++ -c -I.. -I../../include  -DICE_API_EXPORTS  -m32 -ftemplate-depth-128 -Wall -D_REENTRANT -D_M_ARM -Os -DNDEBUG BasicStream.cpp
cc1plus: error: unrecognized command line option "-m32"
make[4]: *** [BasicStream.o] Error 1
make[4]: Leaving directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0/src/IceE'
make[3]: *** [all] Error 1
make[3]: Leaving directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0/src'
make[2]: *** [all] Error 1
make[2]: Leaving directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src/IceE-1.0.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/sean/Desktop/terk-source-code/TeRK-y-0.0.1/embed/src'
make: *** [all] Error 2

```As you can see, it's all fine until i get to the "unrecognized command line option".
I'm using arm-linux-gnueabi package from the ubuntu repository to build this, and i had to create symbolic links to all of the arm-linux-gnueabi programs in /usr/bin because the makefiles are asking for just arm-linux.

Everything else, as far as i can tell, is set to go.

Any help/suggestions?

---

### Post by shiman6 on 2011-07-07
Darn. I posted in the wrong area. Can this thread be moved somehow to programming talk?

---

