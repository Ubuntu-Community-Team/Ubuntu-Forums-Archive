---
title: "Kernel 3.2 rc-1 doesn't want to build the debian way."
date: 2011-11-11
forum: Packaging and Compiling Programs
---

### Post by Psycho Game on 2011-11-11
Hello everybody.

I want to build the kernel 3.2 rc-1 kernel myself, because the mainline repository I think isn't going to offer a i386 version for this version anymore.
The method I was using to build the is the debian way mentioned in: [https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate_Build_Method:_The_Old-Fashioned_Debian_Way)
Now the strange thing is whatever I do to build the Kernel, using the flavor generic, it doesn't want to create the packages.
These are the last few lines before the error occurs, and the error itself.
  CC [M]  fs/xfs/xfs_sysctl.o
  LD [M]  fs/xfs/xfs.o
  LD      fs/built-in.o
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/home/jasper/Downloads/linux-3.2-rc1'
make: *** [/home/jasper/Downloads/linux-3.2-rc1/debian/stamps/stamp-build-generic] Error 2

The problem is only that the compiler doesn't give any clear information about the failure.
Oh yes, the patches I used to get the debians script was from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc1-oneiric/)
Hopefully somebody can help me in building my own i386 kernel.

Greetings Psycho Game

---

