---
title: "Configure error, not sure what to make of it."
date: 2011-12-03
forum: Packaging and Compiling Programs
---

### Post by Gen2ly on 2011-12-03
I'm trying to create a deb package for ntfs-3g that has internal fuse support (this will allow a normal user to mount/unmount a Windows volume from the command line), however I'm getting a configure error that I can't make much sense of.  Here's my process:

```
blddir=~/Downloads/build
pkgname=ntfs-3g
pkgver=$(apt q ntfs-3g | awk '{print $3}' | sed 's/1://') # Unused '1:' before
PKGVER=$(echo $pkgver | sed 's/-.*//')       # Uncompressed build folder name
apt i build-essential fakeroot dpkg-dev lynx
sudo apt-get build-dep $pkgname
[ ! -d $blddir ] && mkdir -p $blddir
cd $blddir
[ ! -d "$pkgname"_$pkgver ] && mkdir "$pkgname"_$PKGVER
cd "$pkgname"_$PKGVER
apt S ntfs-3g
sudo chown -R 1000:1000 .                   # Oddly source is owned by root
cd "$pkgname"-$PKGVER                       # Enter source directory
vim debian/rules                  # --with-fuse=external > --with-fuse=internal
dpkg-buildpackage -rfakeroot -b
```

During configure, it stops with this error:

```
target_cpu='i686'
target_os='linux-gnu'
target_vendor='pc'

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "ntfs-3g"
#define PACKAGE_TARNAME "ntfs-3g"
#define PACKAGE_VERSION "2011.4.12AR.4"
#define PACKAGE_STRING "ntfs-3g 2011.4.12AR.4"
#define PACKAGE_BUGREPORT "ntfs-3g-devel@lists.sf.net"
#define PACKAGE_URL ""
#define PACKAGE "ntfs-3g"
#define VERSION "2011.4.12AR.4"

[COLOR="Sienna"]configure: exit 77[/COLOR]
dh_auto_configure: ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/ntfs-3g --disable-maintainer-mode --disable-dependency-tracking --host=i686-linux-gnu --build=i686-linux-gnu --prefix=/usr --exec-prefix=/ --mandir=${prefix}/share/man --enable-crypto --enable-extras --enable-posix-acls --enable-xattr-mappings --disable-ldconfig --with-fuse=internal CFLAGS=-Wall -g -O2 LDFLAGS=-Wl,-z,defs returned exit code 77
make[1]: *** [override_dh_auto_configure] [COLOR="Sienna"]Error 25[/COLOR]
make[1]: Leaving directory `/home/todd/Downloads/build/ntfs-3g_2011.4.12AR.4/ntfs-3g-2011.4.12AR.4'
make: *** [build] [COLOR="Sienna"]Error 2[/COLOR]
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

Any ideas?

---

### Post by SevenMachines on 2011-12-04
Maybe look at changing
```
 CFLAGS=-Wall -g -O2
```to
```
 CFLAGS="-Wall -g -O2"
```ie, not
```
$ ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/ntfs-3g --disable-maintainer-mode --disable-dependency-tracking --host=i686-linux-gnu --build=i686-linux-gnu --prefix=/usr --exec-prefix=/ --mandir=${prefix}/share/man --enable-crypto --enable-extras --enable-posix-acls --enable-xattr-mappings --disable-ldconfig --with-fuse=internal CFLAGS=-Wall -g -O2 LDFLAGS=-Wl,-z,defs
configure: error: unrecognized option: `-g'
Try `./configure --help' for more information
```but

```
$ ./configure --build=i686-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/ntfs-3g --disable-maintainer-mode --disable-dependency-tracking --host=i686-linux-gnu --build=i686-linux-gnu --prefix=/usr --exec-prefix=/ --mandir=${prefix}/share/man --enable-crypto --enable-extras --enable-posix-acls --enable-xattr-mappings --disable-ldconfig --with-fuse=internal CFLAGS="-Wall -g -O2" LDFLAGS=-Wl,-z,defs
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for i686-linux-gnu-gcc... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
.....
```

---

### Post by Gen2ly on 2011-12-04
Hmm, good thinking with the un-enclosed CFLAGS options.  I tried to enclose them in the debian/rules file but they wouldn't get passed on.  I'm not sure that is the error though for sure because I thought I've seen them un-enclosed before.  Am I wrong?  How should they look in the debian/rules file.  Here's the relevant part of the compiling options file (debian/rules).  I highlighted the CFLAGS options:

```
#!/usr/bin/make -f

SHELL := sh -e

DEB_HOST_GNU_TYPE   ?= $(shell dpkg-architecture -qDEB_HOST_GNU_TYPE)
DEB_BUILD_GNU_TYPE  ?= $(shell dpkg-architecture -qDEB_BUILD_GNU_TYPE)

[COLOR="Sienna"]CFLAGS[/COLOR] = -Wall -g

ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
	[COLOR="Sienna"]CFLAGS[/COLOR] += -O0
else
	[COLOR="Sienna"]CFLAGS[/COLOR] += -O2
endif
ifneq (,$(filter parallel=%,$(DEB_BUILD_OPTIONS)))
        NUMJOBS = $(patsubst parallel=%,%,$(filter parallel=%,$(DEB_BUILD_OPTIONS)))
        MAKEFLAGS += -j$(NUMJOBS)
endif

upstream:
	lynx -dump http://b.andre.pagesperso-orange.fr/changelog.html > debian/local/changelog

%:
	dh ${@} --with autotools_dev

override_dh_auto_configure:
	dh_auto_configure --	--host=$(DEB_HOST_GNU_TYPE) \
				--build=$(DEB_BUILD_GNU_TYPE) \
				--prefix=/usr \
				--exec-prefix=/ \
				--mandir=\$${prefix}/share/man \
				--enable-crypto \
				--enable-extras \
				--enable-posix-acls \
				--enable-xattr-mappings \
				--disable-ldconfig \
				--with-fuse=external \
				[COLOR="Sienna"]CFLAGS[/COLOR]="$([COLOR="Sienna"]CFLAGS[/COLOR])" \
				LDFLAGS="-Wl,-z,defs"
...
```

I changed:

```
CFLAGS = -Wall -g # to
CFLAGS="-Wall -g"
```

but they were Not enclosed when I tried to compile.

**Possibly a second problem??:**

I looked some more at the config.log and also discovered this:

```
configure:3700: error: in `/home/$USER/Downloads/build/ntfs-3g_2011.4.12AR.4/ntfs-3g-2011.4.12AR.4':
configure:3702: error: C compiler cannot create executables
See `config.log' for more details
```

Not sure what to make of this though, I got the development tools I think:

```
libc-bin_2.13-20ubuntu5
libc-dev-bin_2.13-20ubuntu5
libc6_2.13-20ubuntu5
libc6-dev_2.13-20ubuntu5
...
g++_4:4.6.1-2ubuntu5
g++-4.6_4.6.1-9ubuntu3
...
build-essential_11.5ubuntu1  # this this is a meta package
```

Hmmm, any thoughts anyone?

---

### Post by MadCow108 on 2011-12-04
have a look at the config.log
somewhere in there the real error message will be including all parameter that might have caused it. you often have to scroll up quite a bit.

---

### Post by Gen2ly on 2011-12-04
Thanks MadCow.  I think I see what you mean.  I found this:

```
...
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
configure:3611: $? = 0
configure:3600: i686-linux-gnu-gcc -V >&5
[COLOR="Sienna"]i686-linux-gnu-gcc: error: unrecognized option '-V'
i686-linux-gnu-gcc: fatal error: no input files
compilation terminated.[/COLOR]
configure:3611: $? = 4
configure:3600: i686-linux-gnu-gcc -qversion >&5
[COLOR="Sienna"]i686-linux-gnu-gcc: error: unrecognized option '-qversion'
i686-linux-gnu-gcc: fatal error: no input files
compilation terminated.[/COLOR]
configure:3611: $? = 4
[COLOR="Sienna"]configure:3631: checking whether the C compiler works
configure:3653: i686-linux-gnu-gcc -Wall -g -O2  -Wl,-z,defs conftest.c  >&5
conftest.c:18:1: internal compiler error: Segmentation fault
Please submit a full bug report,[/COLOR]
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/ccwVtmwx.out file, please attach this to   your bugreport.
...
```

This seems to be it.  Unfortunately, I'm not entirely sure what to make of it.  To me, it appears like GCC just crashed.  Any ideas?  What can I do from here?

---

### Post by SevenMachines on 2011-12-05
Hi there, no need to chop the log, add it all between code tags or if needs be, add it as an attachment, can't actually see what was happening leading up to the errors!
Your process mentioned in the first post still confuses me a bit, lots of stuff going on and root owning dirs and things. To test out if thats whats broken you might want to try a clean build, this below I know to work to get fuse internal at least here...
```
# Get the source and the build-dep
$ apt-get source ntfs-3g
$ sudo apt-get build-dep ntfs-3g

$ cd ntfs-3g-2011.4.12AR.4/

# Change the fuse option
$ sed -i 's/--with-fuse=external/--with-fuse=internal/g' debian/rules 

# Update the changelog
$ dch -i "Changed fuse option to internal in configuration rules"

#  Build the binaries
$ debuild -b -us -uc
```

---

### Post by MadCow108 on 2011-12-05
> **Gen2ly said:**
> Thanks MadCow.  I think I see what you mean.  I found this:

```
...
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
configure:3611: $? = 0
configure:3600: i686-linux-gnu-gcc -V >&5
[COLOR="Sienna"]i686-linux-gnu-gcc: error: unrecognized option '-V'
i686-linux-gnu-gcc: fatal error: no input files
compilation terminated.[/COLOR]
configure:3611: $? = 4
configure:3600: i686-linux-gnu-gcc -qversion >&5
[COLOR="Sienna"]i686-linux-gnu-gcc: error: unrecognized option '-qversion'
i686-linux-gnu-gcc: fatal error: no input files
compilation terminated.[/COLOR]
configure:3611: $? = 4
[COLOR="Sienna"]configure:3631: checking whether the C compiler works
configure:3653: i686-linux-gnu-gcc -Wall -g -O2  -Wl,-z,defs conftest.c  >&5
conftest.c:18:1: internal compiler error: Segmentation fault
Please submit a full bug report,[/COLOR]
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/ccwVtmwx.out file, please attach this to   your bugreport.
...
```

This seems to be it.  Unfortunately, I'm not entirely sure what to make of it.  To me, it appears like GCC just crashed.  Any ideas?  What can I do from here?

do you know where this -qversion is comming from?

also please upload the temporary file gcc creates, crashes on i686 are rare.

---

### Post by Gen2ly on 2011-12-06
> **SevenMachines said:**
> Hi there, no need to chop the log, add it all between code tags or if needs be, add it as an attachment, can't actually see what was happening leading up to the errors!
Your process mentioned in the first post still confuses me a bit, lots of stuff going on and root owning dirs and things. To test out if thats whats broken you might want to try a clean build, this below I know to work to get fuse internal at least here...
```
# Get the source and the build-dep
$ apt-get source ntfs-3g
$ sudo apt-get build-dep ntfs-3g

$ cd ntfs-3g-2011.4.12AR.4/

# Change the fuse option
$ sed -i 's/--with-fuse=external/--with-fuse=internal/g' debian/rules 

# Update the changelog
$ dch -i "Changed fuse option to internal in configuration rules"

#  Build the binaries
$ debuild -b -us -uc
```

Good suggestion, SevenMachines.  I tried a clean build and your compile method (using debuild) and am getting the same error still.

> **MadCow108 said:**
> do you know where this -qversion is comming from?

also please upload the temporary file gcc creates, crashes on i686 are rare.

From the build directory:

```
grep -Rn qversion .
./config.log:89:configure:3600: i686-linux-gnu-gcc -qversion >&5
./config.log:90:i686-linux-gnu-gcc: error: unrecognized option '-qversion'
./configure:3594:for ac_option in --version -v -V -qversion; do
./configure:4781:for ac_option in --version -v -V -qversion; do
```

Attached the config.log.

---

### Post by SevenMachines on 2011-12-06
Can't reproduce this on i386 or amd64 11.10 clean environments. Maybe have a look at whats happening with
```
$ cat conftest.c 
/* confdefs.h */
 #define PACKAGE_NAME "ntfs-3g"
 #define PACKAGE_TARNAME "ntfs-3g"
 #define PACKAGE_VERSION "2011.4.12AR.4"
 #define PACKAGE_STRING "ntfs-3g 2011.4.12AR.4"
 #define PACKAGE_BUGREPORT "ntfs-3g-devel@lists.sf.net"
 #define PACKAGE_URL ""
 #define PACKAGE "ntfs-3g"
 #define VERSION "2011.4.12AR.4"
 /* end confdefs.h.  */
 
 int
 main ()
 {
 
   ;
   return 0;
 }

$ i686-linux-gnu-gcc -Wall -g -O2  -Wl,-z,defs conftest.c 

```gcc crashing is *unusual*

---

### Post by Gen2ly on 2011-12-06
> **SevenMachines said:**
> Can't reproduce this on i386 or amd64 11.10 clean environments. Maybe have a look at whats happening with
```
$ cat conftest.c 
/* confdefs.h */
 #define PACKAGE_NAME "ntfs-3g"
 #define PACKAGE_TARNAME "ntfs-3g"
 #define PACKAGE_VERSION "2011.4.12AR.4"
 #define PACKAGE_STRING "ntfs-3g 2011.4.12AR.4"
 #define PACKAGE_BUGREPORT "ntfs-3g-devel@lists.sf.net"
 #define PACKAGE_URL ""
 #define PACKAGE "ntfs-3g"
 #define VERSION "2011.4.12AR.4"
 /* end confdefs.h.  */
 
 int
 main ()
 {
 
   ;
   return 0;
 }

$ i686-linux-gnu-gcc -Wall -g -O2  -Wl,-z,defs conftest.c 

```gcc crashing is *unusual*

Man Seven this is good thinking and you hit the nail on the head:

```
# i686-linux-gnu-gcc -Wall -g -O2  -Wl,-z,defs conftest.c
conftest.c:18:2: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/ccyLmuPc.out file, please attach this to your bugreport.
```

The preprocessed source is:

```
# cat /tmp/ccyLmuPc.out 
// /usr/lib/gcc/i686-linux-gnu/4.6.1/cc1 -quiet -imultilib . -imultiarch i386-linux-gnu conftest.c -quiet -dumpbase conftest.c -mtune=generic -march=i686 -auxbase conftest -g -O2 -Wall -fstack-protector -o - -frandom-seed=0
# 1 "conftest.c"
# 1 "/home/todd/Downloads/build//"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "conftest.c"
# 12 "conftest.c"
 int
 main ()
 {

   ;
   return 0;
 }
```

GCC looks like it isn't working from the start.  Any ideas why this may be happening?

---

### Post by SevenMachines on 2011-12-06
You might want to try adding verbose output with -v to the previous conftest.c, maybe try a different version of gcc next and see if its just the one version that's broken. I would suspect somethings broken with the toolchain, do other compilations work ok? It may turn out that reinstalling bits of the toolchain is the simplest way forward

---

### Post by Gen2ly on 2011-12-07
> **SevenMachines said:**
> You might want to try adding verbose output with -v to the previous conftest.c, maybe try a different version of gcc next and see if its just the one version that's broken. I would suspect somethings broken with the toolchain, do other compilations work ok? It may turn out that reinstalling bits of the toolchain is the simplest way forward

Thanks SevenMachines.  At the bottom is the output of the attempted compiling of the conftest.c file with the -v/verbose option.  I installed GCC 4.4.6 from the repositories and it compiled fine ([FONT="Fixedsys"]i686-linux-gnu-gcc-4.4 -Wall -g -O2  -Wl,-z,defs conftest.c[/FONT]; gave no errors, and produced a.out).  Looks like this is a problem with the current GCC 4.6.1, or the current GCC 4.6.1 on my system.

How do I revert to the earlier 4.4.6 GCC version (really I just need dpkg-buildpackage to use older GCC 4.4.6 version).  Any idea on how to do this?

Again, appreciate the help.

```
i686-linux-gnu-gcc -v -Wall -g -O2  -Wl,-z,defs conftest.c
Using built-in specs.
COLLECT_GCC=i686-linux-gnu-gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.6.1/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
COLLECT_GCC_OPTIONS='-v' '-Wall' '-g' '-O2' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/i686-linux-gnu/4.6.1/cc1 -quiet -v -imultilib . -imultiarch i386-linux-gnu conftest.c -quiet -dumpbase conftest.c -mtune=generic -march=i686 -auxbase conftest -g -O2 -Wall -version -fstack-protector -o /tmp/ccMRnwg7.s
GNU C (Ubuntu/Linaro 4.6.1-9ubuntu3) version 4.6.1 (i686-linux-gnu)
	compiled by GNU C version 4.6.1, GMP version 5.0.1, MPFR version 3.0.1-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=72 --param ggc-min-heapsize=79620
ignoring nonexistent directory "/usr/local/include/i386-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../i686-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/i686-linux-gnu/4.6.1/include
 /usr/local/include
 /usr/lib/gcc/i686-linux-gnu/4.6.1/include-fixed
 /usr/include/i386-linux-gnu
 /usr/include
End of search list.
GNU C (Ubuntu/Linaro 4.6.1-9ubuntu3) version 4.6.1 (i686-linux-gnu)
	compiled by GNU C version 4.6.1, GMP version 5.0.1, MPFR version 3.0.1-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=72 --param ggc-min-heapsize=79620
Compiler executable checksum: 4563c158c7f73de3aa3de4c02c58d3f9
conftest.c:18:2: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.6/README.Bugs> for instructions.
Preprocessed source stored into /tmp/cceCTXgJ.out file, please attach this to your bugreport.
```

---

### Post by SevenMachines on 2011-12-08
> Looks like this is a problem with the current GCC 4.6.1, or the current GCC 4.6.1 on my system.Although obviously gcc *can* have bugs, it's just *much* more likely to be your system. Have you tried to ?
```
$ sudo apt-get --reinstall gcc-4.6
```
> How do I revert to the earlier 4.4.6 GCC version (really I just need dpkg-buildpackage to use older GCC 4.4.6 version).  Any idea on how to do this?
You could try adding CC=gcc-4.4 to debian/rules, it's a temporary hack though :)
```
override_dh_auto_configure:
        dh_auto_configure --    CC=gcc-4.4 \
                                --host=$(DEB_HOST_GNU_TYPE) \
                                --build=$(DEB_BUILD_GNU_TYPE) \
                                --prefix=/usr \
                                --exec-prefix=/ \
                                --mandir=\$${prefix}/share/man \
                                --enable-crypto \
                                --enable-extras \
                                --enable-posix-acls \
                                --enable-xattr-mappings \
                                --disable-ldconfig \
                                --with-fuse=external \
                                CFLAGS="$(CFLAGS)" \
                                LDFLAGS="-Wl,-z,defs"

```

---

### Post by Gen2ly on 2011-12-08
Haha, got it done.  Appreciate the help, particularly you SevenMachines.

I didn't try to reinstall GCC yet, but will keep that in mind for the future (I had previously just installed GCC and this was my first time using it so for now I'm just gonna assume that something was buggy from the get-go).  

For using a different version compiler I discover that the CC option can be passed to dpkg-buildpackage too:

```
CC=gcc-4.4 dpkg-buildpackage -rfakeroot -b
```

Again, appreciate the help; got the package built.  Wouldn't have been able to do it otherwise.

Thank you.

---

