---
title: "recompile linux-ubuntu-modules for custom kernel"
date: 2007-11-21
forum: Packaging and Compiling Programs
---

### Post by g.eismann on 2007-11-21
Hello,

I have compiled a custom kernel with:
make-kpkg --append-to-version=-foo --revision=1 kernel_image kernel_headers

So I have a kernel package named linux-image-2.6.22.9-foo_1_i386.deb

I need squashfs and unionfs modules from ubuntu-modules, but I dont know how to recompile linux-ubuntu-modules.

I have followed the instructions in  [this post]("http://ubuntuforums.org/showthread.php?t=553800") changing flavours from "generic" to "foo".
It crashes with this error:

```

$ fakeroot debian/rules binary-arch arch=i386 flavours="foo"

rm -rf /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386
install -d /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/firmware/i386
install -d /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/modules/i386
cp debian/d-i/modules/* /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/modules/i386/
cp debian/d-i/firmware/* /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/firmware/i386/
cp debian/d-i/package-list debian/d-i/kernel-versions \
                /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/
ln -s .. /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386/debian
(cd /tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/d-i-i386; kernel-wedge gen-control) > debian/control
Use of uninitialized value in split at /usr/share/kernel-wedge/commands/gen-control line 32, <KVERS> line 10.
Building foo...
make -C /lib/modules/2.6.22-14-foo/build ARCH=i386 M=/tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-foo UBUNTU_FLAVOUR=foo modules
make: *** /lib/modules/2.6.22-14-foo/build: No such file or directory.  Stop.
make: *** [/tmp/test/linux-ubuntu-modules-2.6.22-2.6.22/debian/stamps/stamp-build-foo] Error 2

```

My kernel is 2.6.22.9-foo but its looking for /lib/modules/2.6.22-14-foo/ that is the ubuntu kernel. Why?

 Thanks,
 Eismann.

---

### Post by sachin.kernel on 2007-12-01
I think you need to change the ABI version for lum.
14 is abi version appeneded to it.

See if this link is useful for changing abi version, 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

They have instructions for changing abi version for lrm.

I have built lum but with same "generic" flavour (all by default things). So I dint change abi version....and it built successfully.

Hope this helps,
Sachin

---

