---
title: "backport libdrm from natty to lucid build error"
date: 2011-03-28
forum: Packaging and Compiling Programs
---

### Post by CMatomic on 2011-03-28
I'm trying to do a backport of the natty libdrm for lucid,
but got the following error

```
checking whether gcc supports -Wsign-compare... yes
checking whether gcc supports -Werror-implicit-function-declaration... yes
checking whether gcc supports -Wpointer-arith... yes
checking whether gcc supports -Wwrite-strings... yes
checking whether gcc supports -Wstrict-prototypes... yes
checking whether gcc supports -Wmissing-prototypes... yes
checking whether gcc supports -Wmissing-declarations... yes
checking whether gcc supports -Wnested-externs... yes
checking whether gcc supports -Wpacked... yes
checking whether gcc supports -Wswitch-enum... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wstrict-aliasing=2... yes
checking whether gcc supports -Winit-self... yes
checking whether gcc supports -Wunsafe-loop-optimizations... yes
checking whether gcc supports -Wdeclaration-after-statement... yes
checking whether gcc supports -Wold-style-definition... yes
checking whether gcc supports -Wno-missing-field-initializers... yes
checking whether gcc supports -Wno-unused-parameter... yes
checking whether gcc supports -Wno-attributes... yes
checking whether gcc supports -Wno-long-long... yes
checking whether gcc supports -Winline... yes
checking which warning flags were supported...  -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -Wno-long-long -Winline
checking for CAIRO... no
checking for LIBUDEV... no
checking for native atomic primitives... Intel
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libkms/Makefile
config.status: creating libkms/libkms.pc
config.status: creating intel/Makefile
config.status: creating intel/libdrm_intel.pc
config.status: creating radeon/Makefile
config.status: creating radeon/libdrm_radeon.pc
config.status: creating nouveau/Makefile
config.status: creating nouveau/libdrm_nouveau.pc
config.status: creating tests/Makefile
config.status: creating tests/modeprint/Makefile
config.status: creating tests/modetest/Makefile
config.status: creating tests/kmstest/Makefile
config.status: creating tests/vbltest/Makefile
config.status: creating include/Makefile
config.status: creating include/drm/Makefile
config.status: creating libdrm.pc
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

libdrm 2.4.23 will be compiled with:

  libkms         yes
  Intel API      yes
  vmwgfx API     yes
  Radeon API     yes
  Nouveau API    yes

dh_testdir
cd build && /usr/bin/make
make[1]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
/usr/bin/make  all-recursive
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
Making all in .
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
  CC     libdrm_la-xf86drm.lo
../xf86drm.c: In function 'drmOpenDevice':
../xf86drm.c:308: warning: unused variable 'user'
../xf86drm.c:307: warning: unused variable 'isroot'
../xf86drm.c: In function 'drmAddMap':
../xf86drm.c:967: warning: cast from pointer to integer of different size
../xf86drm.c: In function 'drmRmMap':
../xf86drm.c:975: warning: cast to pointer from integer of different size
../xf86drm.c: In function 'drmAddContextPrivateMapping':
../xf86drm.c:2111: warning: cast to pointer from integer of different size
../xf86drm.c: In function 'drmGetContextPrivateMapping':
../xf86drm.c:2128: warning: cast from pointer to integer of different size
../xf86drm.c: At top level:
../xf86drm.c:272: warning: 'chown_check_return' defined but not used
  CC     libdrm_la-xf86drmHash.lo
  CC     libdrm_la-xf86drmRandom.lo
  CC     libdrm_la-xf86drmSL.lo
../xf86drmSL.c: In function 'drmSLLookupNeighbors':
../xf86drmSL.c:266: warning: unused variable 'list'
../xf86drmSL.c:273: warning: 'update[0]' is used uninitialized in this function
  CC     libdrm_la-xf86drmMode.lo
../xf86drmMode.c:56: warning: return type defaults to 'int'
  CCLD   libdrm.la
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
Making all in libkms
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
  CC     linux.lo
  CC     intel.lo
  CC     api.lo
  CC     vmwgfx.lo
  CC     nouveau.lo
  CCLD   libkms.la
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
Making all in intel
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/intel'
  CC     intel_bufmgr.lo
  CC     intel_bufmgr_fake.lo
  CC     intel_bufmgr_gem.lo
  CC     mm.lo
  CCLD   libdrm_intel.la
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/intel'
Making all in nouveau
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
  CC     nouveau_device.lo
  CC     nouveau_channel.lo
  CC     nouveau_pushbuf.lo
  CC     nouveau_grobj.lo
  CC     nouveau_notifier.lo
  CC     nouveau_bo.lo
  CC     nouveau_resource.lo
  CC     nouveau_reloc.lo
  CCLD   libdrm_nouveau.la
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
Making all in radeon
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
  CC     radeon_bo_gem.lo
  CC     radeon_cs_gem.lo
../../radeon/radeon_cs_gem.c:333: warning: 'cs_gem_dump_bof' defined but not used
  CC     radeon_cs_space.lo
  CC     radeon_bo.lo
  CC     radeon_cs.lo
  CC     bof.lo
../../radeon/bof.c: In function 'bof_object_get':
../../radeon/bof.c:68: warning: cannot optimize loop, the loop counter may overflow
  CCLD   libdrm_radeon.la
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
Making all in tests
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests'
Making all in kmstest
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
  CC     main.o
  CCLD   kmstest
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests'
Making all in include
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include'
Making all in drm
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
make[1]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
>build-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_prep
for file in libdrm-intel1.install libdrm-nouveau1a.install \
	            libdrm-radeon1.install libdrm2.install libkms1.install \
	            libdrm-dev.links; \
	do \
		sed -e"s,\${DEB_HOST_MULTIARCH},amd64,g" \
			debian/${file}.in > debian/$file; \
	done
dh_installdirs
cd build && /usr/bin/make install DESTDIR=/tmp/buildd/libdrm-2.4.23/debian/tmp
make[1]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
Making install in .
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/amd64" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libdrm.la '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64'
libtool: install: /usr/bin/install -c .libs/libdrm.so.2.4.0 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm.so.2.4.0
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm.so.2.4.0 libdrm.so.2 || { rm -f libdrm.so.2 && ln -s libdrm.so.2.4.0 libdrm.so.2; }; })
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm.so.2.4.0 libdrm.so || { rm -f libdrm.so && ln -s libdrm.so.2.4.0 libdrm.so; }; })
libtool: install: /usr/bin/install -c .libs/libdrm.lai /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm.la
libtool: install: /usr/bin/install -c .libs/libdrm.a /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm.a
libtool: install: chmod 644 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm.a
libtool: install: ranlib /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm.a
libtool: install: warning: remember to run `libtool --finish /usr/lib/amd64'
test -z "/usr/include" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include"
 /usr/bin/install -c -m 644 ../xf86drm.h ../xf86drmMode.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include'
test -z "/usr/lib/amd64/pkgconfig" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig"
 /usr/bin/install -c -m 644 libdrm.pc '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
Making install in libkms
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/amd64" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libkms.la '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64'
libtool: install: warning: relinking `libkms.la'
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/build/libkms; /bin/bash /tmp/buildd/libdrm-2.4.23/build/libtool  --silent --tag CC --mode=relink gcc -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -Wno-long-long -Winline -I../../include/drm -I../.. -Wall -g -O2 -version-number 1:0:0 -no-undefined -Wl,-Bsymbolic-functions -o libkms.la -rpath /usr/lib/amd64 linux.lo intel.lo api.lo vmwgfx.lo nouveau.lo ../libdrm.la -inst-prefix-dir /tmp/buildd/libdrm-2.4.23/debian/tmp)
libtool: install: /usr/bin/install -c .libs/libkms.so.1.0.0T /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libkms.so.1.0.0
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libkms.so.1.0.0 libkms.so.1 || { rm -f libkms.so.1 && ln -s libkms.so.1.0.0 libkms.so.1; }; })
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libkms.so.1.0.0 libkms.so || { rm -f libkms.so && ln -s libkms.so.1.0.0 libkms.so; }; })
libtool: install: /usr/bin/install -c .libs/libkms.lai /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libkms.la
libtool: install: /usr/bin/install -c .libs/libkms.a /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libkms.a
libtool: install: chmod 644 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libkms.a
libtool: install: ranlib /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libkms.a
libtool: install: warning: remember to run `libtool --finish /usr/lib/amd64'
test -z "/usr/include/libkms" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libkms"
 /usr/bin/install -c -m 644 ../../libkms/libkms.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libkms'
test -z "/usr/lib/amd64/pkgconfig" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig"
 /usr/bin/install -c -m 644 libkms.pc '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/libkms'
Making install in intel
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/intel'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/intel'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/amd64" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libdrm_intel.la '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64'
libtool: install: warning: relinking `libdrm_intel.la'
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/build/intel; /bin/bash /tmp/buildd/libdrm-2.4.23/build/libtool  --silent --tag CC --mode=relink gcc -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -Wno-long-long -Winline -I../.. -I../../intel -I../../include/drm -Wall -g -O2 -version-number 1:0:0 -no-undefined -Wl,-Bsymbolic-functions -o libdrm_intel.la -rpath /usr/lib/amd64 intel_bufmgr.lo intel_bufmgr_fake.lo intel_bufmgr_gem.lo mm.lo ../libdrm.la -lrt -inst-prefix-dir /tmp/buildd/libdrm-2.4.23/debian/tmp)
libtool: install: /usr/bin/install -c .libs/libdrm_intel.so.1.0.0T /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_intel.so.1.0.0
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_intel.so.1.0.0 libdrm_intel.so.1 || { rm -f libdrm_intel.so.1 && ln -s libdrm_intel.so.1.0.0 libdrm_intel.so.1; }; })
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_intel.so.1.0.0 libdrm_intel.so || { rm -f libdrm_intel.so && ln -s libdrm_intel.so.1.0.0 libdrm_intel.so; }; })
libtool: install: /usr/bin/install -c .libs/libdrm_intel.lai /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_intel.la
libtool: install: /usr/bin/install -c .libs/libdrm_intel.a /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_intel.a
libtool: install: chmod 644 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_intel.a
libtool: install: ranlib /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_intel.a
libtool: install: warning: remember to run `libtool --finish /usr/lib/amd64'
test -z "/usr/include/libdrm" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm"
 /usr/bin/install -c -m 644 ../../intel/intel_bufmgr.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm'
test -z "/usr/lib/amd64/pkgconfig" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig"
 /usr/bin/install -c -m 644 libdrm_intel.pc '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/intel'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/intel'
Making install in nouveau
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/amd64" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libdrm_nouveau.la '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64'
libtool: install: warning: relinking `libdrm_nouveau.la'
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/build/nouveau; /bin/bash /tmp/buildd/libdrm-2.4.23/build/libtool  --silent --tag CC --mode=relink gcc -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -Wno-long-long -Winline -I../.. -I../../nouveau -I../../include/drm -Wall -g -O2 -version-number 1:0:0 -no-undefined -Wl,-Bsymbolic-functions -o libdrm_nouveau.la -rpath /usr/lib/amd64 nouveau_device.lo nouveau_channel.lo nouveau_pushbuf.lo nouveau_grobj.lo nouveau_notifier.lo nouveau_bo.lo nouveau_resource.lo nouveau_reloc.lo ../libdrm.la -inst-prefix-dir /tmp/buildd/libdrm-2.4.23/debian/tmp)
libtool: install: /usr/bin/install -c .libs/libdrm_nouveau.so.1.0.0T /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_nouveau.so.1.0.0
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_nouveau.so.1.0.0 libdrm_nouveau.so.1 || { rm -f libdrm_nouveau.so.1 && ln -s libdrm_nouveau.so.1.0.0 libdrm_nouveau.so.1; }; })
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_nouveau.so.1.0.0 libdrm_nouveau.so || { rm -f libdrm_nouveau.so && ln -s libdrm_nouveau.so.1.0.0 libdrm_nouveau.so; }; })
libtool: install: /usr/bin/install -c .libs/libdrm_nouveau.lai /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_nouveau.la
libtool: install: /usr/bin/install -c .libs/libdrm_nouveau.a /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_nouveau.a
libtool: install: chmod 644 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_nouveau.a
libtool: install: ranlib /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_nouveau.a
libtool: install: warning: remember to run `libtool --finish /usr/lib/amd64'
test -z "/usr/include/nouveau" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/nouveau"
 /usr/bin/install -c -m 644 ../../nouveau/nouveau_device.h ../../nouveau/nouveau_channel.h ../../nouveau/nouveau_grobj.h ../../nouveau/nouveau_notifier.h ../../nouveau/nouveau_pushbuf.h ../../nouveau/nouveau_bo.h ../../nouveau/nouveau_resource.h ../../nouveau/nouveau_reloc.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/nouveau'
test -z "/usr/include/libdrm" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm"
 /usr/bin/install -c -m 644 ../../nouveau/nouveau_drmif.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm'
test -z "/usr/lib/amd64/pkgconfig" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig"
 /usr/bin/install -c -m 644 libdrm_nouveau.pc '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/nouveau'
Making install in radeon
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/amd64" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libdrm_radeon.la '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64'
libtool: install: warning: relinking `libdrm_radeon.la'
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/build/radeon; /bin/bash /tmp/buildd/libdrm-2.4.23/build/libtool  --silent --tag CC --mode=relink gcc -Wall -Wextra -Wsign-compare -Werror-implicit-function-declaration -Wpointer-arith -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wpacked -Wswitch-enum -Wmissing-format-attribute -Wstrict-aliasing=2 -Winit-self -Wunsafe-loop-optimizations -Wdeclaration-after-statement -Wold-style-definition -Wno-missing-field-initializers -Wno-unused-parameter -Wno-attributes -Wno-long-long -Winline -I../.. -I../../radeon -I../../include/drm -Wall -g -O2 -version-number 1:0:0 -no-undefined -Wl,-Bsymbolic-functions -o libdrm_radeon.la -rpath /usr/lib/amd64 radeon_bo_gem.lo radeon_cs_gem.lo radeon_cs_space.lo radeon_bo.lo radeon_cs.lo bof.lo ../libdrm.la -inst-prefix-dir /tmp/buildd/libdrm-2.4.23/debian/tmp)
libtool: install: /usr/bin/install -c .libs/libdrm_radeon.so.1.0.0T /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_radeon.so.1.0.0
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_radeon.so.1.0.0 libdrm_radeon.so.1 || { rm -f libdrm_radeon.so.1 && ln -s libdrm_radeon.so.1.0.0 libdrm_radeon.so.1; }; })
libtool: install: (cd /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64 && { ln -s -f libdrm_radeon.so.1.0.0 libdrm_radeon.so || { rm -f libdrm_radeon.so && ln -s libdrm_radeon.so.1.0.0 libdrm_radeon.so; }; })
libtool: install: /usr/bin/install -c .libs/libdrm_radeon.lai /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_radeon.la
libtool: install: /usr/bin/install -c .libs/libdrm_radeon.a /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_radeon.a
libtool: install: chmod 644 /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_radeon.a
libtool: install: ranlib /tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/libdrm_radeon.a
libtool: install: warning: remember to run `libtool --finish /usr/lib/amd64'
test -z "/usr/include/libdrm" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm"
 /usr/bin/install -c -m 644 ../../radeon/radeon_bo.h ../../radeon/radeon_cs.h ../../radeon/radeon_bo_gem.h ../../radeon/radeon_cs_gem.h ../../radeon/radeon_bo_int.h ../../radeon/radeon_cs_int.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm'
test -z "/usr/lib/amd64/pkgconfig" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig"
 /usr/bin/install -c -m 644 libdrm_radeon.pc '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/lib/amd64/pkgconfig'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/radeon'
Making install in tests
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests'
Making install in kmstest
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests/kmstest'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/tests'
Making install in include
make[2]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include'
Making install in drm
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/libdrm" || /bin/mkdir -p "/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm"
 /usr/bin/install -c -m 644 ../../../include/drm/drm.h ../../../include/drm/drm_mode.h ../../../include/drm/drm_sarea.h ../../../include/drm/i915_drm.h ../../../include/drm/mga_drm.h ../../../include/drm/nouveau_drm.h ../../../include/drm/r128_drm.h ../../../include/drm/radeon_drm.h ../../../include/drm/savage_drm.h ../../../include/drm/sis_drm.h ../../../include/drm/via_drm.h ../../../include/drm/mach64_drm.h ../../../include/drm/vmwgfx_drm.h '/tmp/buildd/libdrm-2.4.23/debian/tmp/usr/include/libdrm'
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include/drm'
make[3]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[4]: Entering directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[3]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[2]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build/include'
make[1]: Leaving directory `/tmp/buildd/libdrm-2.4.23/build'
dh_testdir -s
dh_testroot -s
dh_installchangelogs
dh_installdocs -s
dh_installexamples -s
dh_install -s --sourcedir=debian/tmp -X.la --fail-missing
dh_link -s
dh_strip -plibdrm2 --dbg-package=libdrm2-dbg
dh_strip -plibdrm-intel1 --dbg-package=libdrm-intel1-dbg
dh_strip -plibdrm-nouveau1a --dbg-package=libdrm-nouveau1a-dbg
dh_strip -plibdrm-radeon1 --dbg-package=libdrm-radeon1-dbg
dh_strip -p libkms1 --dbg-package=libkms1-dbg
dh_strip -s --remaining-packages
dh_compress -s
dh_fixperms -s
dh_makeshlibs -plibdrm2 -V'libdrm2 (>= 2.4.17)' -- -c4
dpkg-gensymbols: warning: some libraries disappeared in the symbols file: libdrm.so.2
dpkg-gensymbols: warning:  doesn't match completely debian/libdrm2.symbols
--- debian/libdrm2.symbols (libdrm2 amd64)
+++ dpkg-gensymbols9LHFAL	2011-03-28 17:00:56.602932655 +0000
@@ -1,136 +0,0 @@
-libdrm.so.2 libdrm2 #MINVER#
- drmAddBufs@Base 2.3.1
- drmAddContextPrivateMapping@Base 2.3.1
- drmAddContextTag@Base 2.3.1
- drmAddMap@Base 2.3.1
- drmAgpAcquire@Base 2.3.1
- drmAgpAlloc@Base 2.3.1
- drmAgpBase@Base 2.3.1
- drmAgpBind@Base 2.3.1
- drmAgpDeviceId@Base 2.3.1
- drmAgpEnable@Base 2.3.1
- drmAgpFree@Base 2.3.1
- drmAgpGetMode@Base 2.3.1
- drmAgpMemoryAvail@Base 2.3.1
- drmAgpMemoryUsed@Base 2.3.1
- drmAgpRelease@Base 2.3.1
- drmAgpSize@Base 2.3.1
- drmAgpUnbind@Base 2.3.1
- drmAgpVendorId@Base 2.3.1
- drmAgpVersionMajor@Base 2.3.1
- drmAgpVersionMinor@Base 2.3.1
- drmAllocCpy@Base 2.4.3
- drmAuthMagic@Base 2.3.1
- drmAvailable@Base 2.3.1
- drmCheckModesettingSupported@Base 2.4.3
- drmClose@Base 2.3.1
- drmCloseOnce@Base 2.3.1
- drmCommandNone@Base 2.3.1
- drmCommandRead@Base 2.3.1
- drmCommandWrite@Base 2.3.1
- drmCommandWriteRead@Base 2.3.1
- drmCreateContext@Base 2.3.1
- drmCreateDrawable@Base 2.3.1
- drmCtlInstHandler@Base 2.3.1
- drmCtlUninstHandler@Base 2.3.1
- drmDMA@Base 2.3.1
- drmDelContextTag@Base 2.3.1
- drmDestroyContext@Base 2.3.1
- drmDestroyDrawable@Base 2.3.1
- drmDropMaster@Base 2.4.3
- drmError@Base 2.3.1
- drmFinish@Base 2.3.1
- drmFree@Base 2.3.1
- drmFreeBufs@Base 2.3.1
- drmFreeBusid@Base 2.3.1
- drmFreeReservedContextList@Base 2.3.1
- drmFreeVersion@Base 2.3.1
- drmGetBufInfo@Base 2.3.1
- drmGetBusid@Base 2.3.1
- drmGetClient@Base 2.3.1
- drmGetContextFlags@Base 2.3.1
- drmGetContextPrivateMapping@Base 2.3.1
- drmGetContextTag@Base 2.3.1
- drmGetDeviceNameFromFd@Base 2.4.16
- drmGetEntry@Base 2.3.1
- drmGetHashTable@Base 2.3.1
- drmGetInterruptFromBusID@Base 2.3.1
- drmGetLibVersion@Base 2.3.1
- drmGetLock@Base 2.3.1
- drmGetMagic@Base 2.3.1
- drmGetMap@Base 2.3.1
- drmGetReservedContextList@Base 2.3.1
- drmGetStats@Base 2.3.1
- drmGetVersion@Base 2.3.1
- drmHandleEvent@Base 2.4.16
- drmHashCreate@Base 2.3.1
- drmHashDelete@Base 2.3.1
- drmHashDestroy@Base 2.3.1
- drmHashFirst@Base 2.3.1
- drmHashInsert@Base 2.3.1
- drmHashLookup@Base 2.3.1
- drmHashNext@Base 2.3.1
- drmIoctl@Base 2.4.3
- drmMalloc@Base 2.3.1
- drmMap@Base 2.3.1
- drmMapBufs@Base 2.3.1
- drmMarkBufs@Base 2.3.1
- drmModeAddFB@Base 2.4.3
- drmModeAttachMode@Base 2.4.3
- drmModeConnectorSetProperty@Base 2.4.3
- drmModeCrtcGetGamma@Base 2.4.3
- drmModeCrtcSetGamma@Base 2.4.3
- drmModeDetachMode@Base 2.4.3
- drmModeDirtyFB@Base 2.4.17
- drmModeFreeConnector@Base 2.4.3
- drmModeFreeCrtc@Base 2.4.3
- drmModeFreeEncoder@Base 2.4.3
- drmModeFreeFB@Base 2.4.3
- drmModeFreeModeInfo@Base 2.4.3
- drmModeFreeProperty@Base 2.4.3
- drmModeFreePropertyBlob@Base 2.4.3
- drmModeFreeResources@Base 2.4.3
- drmModeGetConnector@Base 2.4.3
- drmModeGetCrtc@Base 2.4.3
- drmModeGetEncoder@Base 2.4.3
- drmModeGetFB@Base 2.4.3
- drmModeGetProperty@Base 2.4.3
- drmModeGetPropertyBlob@Base 2.4.3
- drmModeGetResources@Base 2.4.3
- drmModeMoveCursor@Base 2.4.3
- drmModePageFlip@Base 2.4.17
- drmModeRmFB@Base 2.4.3
- drmModeSetCrtc@Base 2.4.3
- drmModeSetCursor@Base 2.4.3
- drmMsg@Base 2.4.1
- drmOpen@Base 2.3.1
- drmOpenControl@Base 2.4.3
- drmOpenOnce@Base 2.3.1
- drmRandom@Base 2.3.1
- drmRandomCreate@Base 2.3.1
- drmRandomDestroy@Base 2.3.1
- drmRandomDouble@Base 2.3.1
- drmRmMap@Base 2.3.1
- drmSLCreate@Base 2.3.1
- drmSLDelete@Base 2.3.1
- drmSLDestroy@Base 2.3.1
- drmSLDump@Base 2.3.1
- drmSLFirst@Base 2.3.1
- drmSLInsert@Base 2.3.1
- drmSLLookup@Base 2.3.1
- drmSLLookupNeighbors@Base 2.3.1
- drmSLNext@Base 2.3.1
- drmScatterGatherAlloc@Base 2.3.1
- drmScatterGatherFree@Base 2.3.1
- drmSetBusid@Base 2.3.1
- drmSetContextFlags@Base 2.3.1
- drmSetDebugMsgFunction@Base 2.3.1
- drmSetInterfaceVersion@Base 2.3.1
- drmSetMaster@Base 2.4.3
- drmSetServerInfo@Base 2.3.1
- drmSwitchToContext@Base 2.3.1
- drmUnlock@Base 2.3.1
- drmUnmap@Base 2.3.1
- drmUnmapBufs@Base 2.3.1
- drmUpdateDrawableInfo@Base 2.3.1
- drmWaitVBlank@Base 2.3.1
dh_makeshlibs: dpkg-gensymbols -plibdrm2 -Idebian/libdrm2.symbols -Pdebian/libdrm2 -c4 returned exit code 3
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//11512 and its subdirectories
codexlibre@tonignome-laptop:~/CodigosFonte/libdrm$ 
```

---

### Post by MadCow108 on 2011-03-28
the library you are compiling is missing some symbols set in debian/libdrm2.symbols
I don't know why they are missing, possibly they are only included when other newer software is available too (like X?)

to solve this I suggest one of the following:
use the symbols file of the lucid version, if it works you might be in luck and the version is ABI and API compatible and you can perhaps continue without further changes.
But its still risky, the symbol file is far from a foolproof measure to test binary compatibility. (a better tool is [http://ispras.linux-foundation.org/index.php/ABI_compliance_checker](http://ispras.linux-foundation.org/index.php/ABI_compliance_checker))

Better (and necessary when the lucid symbol file does not solve the issue):
Adapt the symbol file to the symbols actually in the library and change the soversion + package name to allow parallel installation of the two incompatible versions (lucid and natty)

Then rebuild all wanted applications depending on libdrm so they use the new API/ABI of the library

---

