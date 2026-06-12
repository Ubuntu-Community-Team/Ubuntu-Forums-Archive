---
title: "complie kernel rt flavour"
date: 2008-05-23
forum: Packaging and Compiling Programs
---

### Post by debhalrlock on 2008-05-23
Hi folks,

I'm trying to compile the kernel-rt follow this guide [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

I get the git repository
git-clone git://kernel.ubuntu.com/abogani/ubuntu-hardy-rt.git

then I make menuconfig to create my .config file

I copy .config to debian/binary-custom.d/rt/config.i386

I run
AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-rt

and I have this error
```
scripts/kconfig/conf -s arch/x86/Kconfig
  Using /usr/src/kernel/ubuntu-hardy-rt/debian/build/custom-source-rt as source for kernel
  /usr/src/kernel/ubuntu-hardy-rt/debian/build/custom-source-rt is not clean, please run 'make mrproper'
  in the '/usr/src/kernel/ubuntu-hardy-rt/debian/build/custom-source-rt' directory.
make[4]: *** [prepare3] Error 1
make[3]: *** [sub-make] Error 2
make[2]: *** [prepare] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/kernel/ubuntu-hardy-rt/debian/build/custom-source-rt'
make: *** [/usr/src/kernel/ubuntu-hardy-rt/debian/stamps/stamp-custom-prepare-rt] Error 2
```


then i run make mrproper in /usr/src/kernel/ubuntu-hardy-rt/debian/build/custom-source-rt but i have not change.


Someone can help me?

Thanks
debharlock

---

