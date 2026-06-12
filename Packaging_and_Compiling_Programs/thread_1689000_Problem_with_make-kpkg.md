---
title: "Problem with make-kpkg"
date: 2011-02-16
forum: Packaging and Compiling Programs
---

### Post by nukem996 on 2011-02-16
I am trying compile the vanilla 2.6.37 kernel with some changes I've made for testing into a Debian package. When I used to do kernel development work on Debian I would always use make-kpkg so I thought I'd try it again. However I am running into a really weird error.

The command I am using to compile is

```

fakeroot make-kpkg --append_to_version "-anfs" --initrd kernel_image kernel_debug kernel_headers

```The kernel itself compiles fine but when it goes to make the package I get the following error.

```

install -p    -o root -g root  -m  644 ./debian/templates.master /home/nuke/ANFS-kernel/debian/linux-image-2.6.37-anfs+/DEBIAN/templates
dpkg-gencontrol -DArchitecture=amd64 -isp         \
            -plinux-image-2.6.37-anfs+ -P/home/nuke/ANFS-kernel/debian/linux-image-2.6.37-anfs+/
dpkg-gencontrol: error: package linux-image-2.6.37-anfs+ not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.37-anfs+] Error 255
make[2]: Leaving directory `/home/nuke/ANFS-kernel'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.37-anfs+] Error 2
make[1]: Leaving directory `/home/nuke/ANFS-kernel'
make: *** [kernel_image] Error 2

```I tried adding --revision 1 but I still get the same error. What am I doing wrong?

Can someone please help me?

Thanks

---

### Post by nukem996 on 2011-02-17
I was able to fix it by commenting out the last line(the return value) in scripts/setlocalversion. An explanation can be found here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=591793](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=591793)

---

