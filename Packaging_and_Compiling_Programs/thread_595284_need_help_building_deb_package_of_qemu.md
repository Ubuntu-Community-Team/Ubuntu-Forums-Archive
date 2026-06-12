---
title: "need help building deb package of qemu"
date: 2007-10-28
forum: Packaging and Compiling Programs
---

### Post by go_beep_yourself on 2007-10-28
I am trying to create a deb of qemu without using checkinstall. Here is what I have done. I followed this guide.

[http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source](http://www.quietearth.us/articles/2006/08/16/Building-deb-package-from-source)

Why did it not work? What has gone wrong?

root@ubuntu:/tmp# cd qemu-0.9.0
root@ubuntu:/tmp/qemu-0.9.0# ls
aes.c          cpu-all.h          LICENSE              softmmu_template.h
aes.h          cpu-defs.h         linux-user           sparc64.ld
alpha-dis.c    cpu-exec.c         loader.c             sparc-dis.c
alpha.ld       cutils.c           m68k-dis.c           sparc.ld
a.out.h        darwin-user        m68k.ld              tap-win32.c
arm-dis.c      disas.c            Makefile             target-arm
arm.ld         disas.h            Makefile.target      target-i386
arm-semi.c     dis-asm.h          mips-dis.c           target-m68k
audio          dyngen.c           monitor.c            target-mips
block-bochs.c  dyngen-exec.h      osdep.c              target-ppc
block.c        dyngen.h           osdep.h              target-sh4
block-cloop.c  dyngen-op.h        pc-bios              target-sparc
block-cow.c    elf.h              ppc-dis.c            tests
block-dmg.c    elf_ops.h          ppc.ld               texi2pod.pl
block_int.h    exec-all.h         qemu-binfmt-conf.sh  thunk.c
block-qcow2.c  exec.c             qemu-doc.texi        thunk.h
block-qcow.c   fpu                qemu-img.c           TODO
block-raw.c    gdbstub.c          qemu-img.texi        translate-all.c
block-vmdk.c   gdbstub.h          qemu_socket.h        translate-op.c
block-vpc.c    hostregs_helper.h  qemu-tech.texi       usb-linux.c
block-vvfat.c  hw                 readline.c           VERSION
bswap.h        i386-dis.c         README               vgafont.h
Changelog      i386.ld            s390.ld              vl.c
check_ops.sh   i386-vl.ld         sdl.c                vl.h
cocoa.m        ia64.ld            sdl_keysym.h         vnc.c
configure      keymaps            sh4-dis.c            vnchextile.h
console.c      keymaps.c          slirp                vnc_keysym.h
COPYING        kqemu.c            softmmu_exec.h       x86_64.ld
COPYING.LIB    kqemu.h            softmmu_header.h     x_keymap.c
root@ubuntu:/tmp/qemu-0.9.0# dh_make
822-date: warning: This program is deprecated. Please use 'date -R' instead.

Type of package: single binary, multiple binary, library, kernel module or cdbs?
 [s/m/l/k/b] s

Maintainer name : root
Email-Address   : root@ubuntu 
Date            : Sun, 28 Oct 2007 16:43:53 -0500
Package Name    : qemu
Version         : 0.9.0
License         : blank
Type of Package : Single
Hit <enter> to confirm: 
Could not find qemu_0.9.0.orig.tar.gz
Either specify an alternate file to use with -f,
or add --createorig to create one.
root@ubuntu:/tmp/qemu-0.9.0# dh_make --createorig
822-date: warning: This program is deprecated. Please use 'date -R' instead.

Type of package: single binary, multiple binary, library, kernel module or cdbs?
 [s/m/l/k/b] s

Maintainer name : root
Email-Address   : root@ubuntu 
Date            : Sun, 28 Oct 2007 16:44:29 -0500
Package Name    : qemu
Version         : 0.9.0
License         : blank
Type of Package : Single
Hit <enter> to confirm: 
Done. Please edit the files in the debian/ subdirectory now. qemu
uses a configure script, so you probably don't have to edit the Makefiles.
root@ubuntu:/tmp/qemu-0.9.0# cd debian/
root@ubuntu:/tmp/qemu-0.9.0/debian# vim  
changelog           emacsen-remove.ex   postrm.ex
compat              emacsen-startup.ex  preinst.ex
control             init.d.ex           prerm.ex
copyright           manpage.1.ex        qemu-default.ex
cron.d.ex           manpage.sgml.ex     qemu.doc-base.EX
dirs                manpage.xml.ex      README.Debian
docs                menu.ex             rules
emacsen-install.ex  postinst.ex         watch.ex
root@ubuntu:/tmp/qemu-0.9.0/debian# vim control 
root@ubuntu:/tmp/qemu-0.9.0/debian# dpkg-buildpackage -rfakeroot
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
root@ubuntu:/tmp/qemu-0.9.0/debian# cd ..
root@ubuntu:/tmp/qemu-0.9.0# dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is qemu
dpkg-buildpackage: source version is 0.9.0-1
dpkg-buildpackage: source changed by root <root@ubuntu>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 0.9.0-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/tmp/qemu-0.9.0'
Makefile:3: config-host.mak: No such file or directory
make[1]: *** No rule to make target `config-host.mak'.  Stop.
make[1]: Leaving directory `/tmp/qemu-0.9.0'
make: [clean] Error 2 (ignored)
rm -f config.sub config.guess
dh_clean 
 dpkg-source -b qemu-0.9.0
dpkg-source: building qemu in qemu_0.9.0.orig.tar.gz
dpkg-source: building qemu in qemu_0.9.0-1.diff.gz
dpkg-source: building qemu in qemu_0.9.0-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info CFLAGS="-Wall -g -O2" LDFLAGS="-Wl,-z,defs"
WARNING: "gcc" looks like gcc 4.x
Looking for gcc 3.x
./configure: 372: Syntax error: Bad fd number
make: *** [config.status] Error 2
root@ubuntu:/tmp/qemu-0.9.0#

---

### Post by ridgid on 2007-11-26
I was compiling qemu and had this problem
"./configure: 372: Syntax error: Bad fd number"

found this:
 sudo rm /bin/sh
 sudo ln -s /bin/bash /bin/sh

my thanks to HymnToLife

from 
[http://ubuntuforums.org/archive/index.php/t-382548.html](http://ubuntuforums.org/archive/index.php/t-382548.html)

---

### Post by dholbach on 2007-11-27
> **ridgid said:**
>  sudo rm /bin/sh
 sudo ln -s /bin/bash /bin/sh


DON'T DO THIS!

---

### Post by aaoberon on 2007-12-20
I had this problem with the qemu source tarball from the official Qemu site: "Syntax error: Bad fd number"  


A better way to fix this is to edit the ./configure file and change the first line from "#!/bin/sh" to "#!/bin/bash".

---

