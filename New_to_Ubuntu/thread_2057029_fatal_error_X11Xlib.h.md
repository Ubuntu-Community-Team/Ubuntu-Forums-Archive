---
title: "fatal error: X11/Xlib.h:"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Sunny1234 on 2012-09-12
hi. i am using ubuntu 12.04 and trying to install NS2.35
for that matter i downloaded ns-allinone-2.35, unzipped it, started installation, the installation went well until it gave an error message and stopped. the error message is as follows:

: fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make: *** [tk3d.o] Error 1
tk8.5.10 make failed! Exiting ...

I'm pretty sure that I do have Xlib.h at the right place. i also tried to do this 'sudo apt-get install libx11-dev' but it returned me the following:

"Package libx11-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libx11-dev' has no installation candidate

"


in desperate search to an immediate solution.

---

### Post by jerrrys on 2012-09-12
edit

wrong reply, sorry

---

### Post by dodo3773 on 2012-09-12
Is this what you are looking for?:

[https://launchpad.net/ubuntu/precise/amd64/libx11-6](https://launchpad.net/ubuntu/precise/amd64/libx11-6)

If that's not it then just do a search for libx11 or x11 in your package manager.

---

### Post by Sunny1234 on 2012-09-13
while installing, tcl was installed successfully, but when it came to tk, it gave the following messages:

============================================================
* Build Tk8.5.10
============================================================
rm -f *.a *.o libtk* core errs *~ \#* TAGS *.E a.out \
		errors wish tktest lib.exp Tk *.rsrc
rm -rf Makefile config.status config.cache config.log tkConfig.sh \
		SCRPtk.* prototype tkConfig.h *.plist Tk.framework
**./install: 439: ./install: autoconf: not found**
checking for Tcl configuration... found /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tcl8.5.10/unix/tclConfig.sh
checking for existence of /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tcl8.5.10/unix/tclConfig.sh... loading
checking for tclsh... /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/bin/tclsh8.5
checking for tclsh in Tcl build directory... /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tcl8.5.10/unix/tclsh
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for stdlib.h... (cached) yes
checking if the compiler understands -pipe... yes
checking for building with threads... no (default)
checking how to build libraries... static
checking for ranlib... ranlib
[B]checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no[/B]
checking if compiler supports visibility "hidden"... yes
checking if rpath support is requested... yes
checking system version... Linux-3.2.0-26-generic
checking for dlopen in -ldl... yes
checking for ar... ar
checking for build with symbols... no
checking for required early compiler flags...  _LARGEFILE64_SOURCE
checking for 64-bit integer type... using long
checking whether byte ordering is bigendian... no
checking for fd_set in sys/types... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for strtod... yes
checking for Solaris2.4/Tru64 strtod bugs... ok
checking for mode_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for intptr_t... yes
checking for uintptr_t... yes
checking pw_gecos in struct pwd... yes
**checking for X... no**
[B]checking for X11 header files... couldn't find any!
checking for X11 libraries... checking for XCreateWindow in -lXwindow... no
could not find any!  Using -lX11.
checking for main in -lXbsd... no
checking whether to try to use XScreenSaver... no
checking whether to use xft... no
checking whether char is unsigned... no
configure: creating ./config.status[/B]
config.status: creating Makefile
config.status: creating tkConfig.sh
gcc -c -O2  -pipe  -Wall -fPIC -I/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../unix -I/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../generic -I/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../bitmaps -I/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tcl8.5.10/generic -I/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tcl8.5.10/unix  -DPACKAGE_NAME=\"tk\" -DPACKAGE_TARNAME=\"tk\" -DPACKAGE_VERSION=\"8.5\" -DPACKAGE_STRING=\"tk\ 8.5\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1 -DSTATIC_BUILD=1 -DMODULE_SCOPE=extern\ __attribute__\(\(__visibility__\(\"hidden\"\)\)\) -DTCL_SHLIB_EXT=\".so\" -DTCL_CFG_OPTIMIZED=1 -DTCL_CFG_DEBUG=1 -D_LARGEFILE64_SOURCE=1 -DTCL_WIDE_INT_IS_LONG=1 -DHAVE_SYS_TIME_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_INTPTR_T=1 -DHAVE_UINTPTR_T=1 -DHAVE_PW_GECOS=1      -DTCL_NO_DEPRECATED    /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../generic/tk3d.c
In file included from /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../generic/tkInt.h:19:0,
                 from /home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../generic/tk3d.c:14:
/home/ahsen/.local/share/Trash/files/ns-allinone-2.3.35/tk8.5.10/unix/../generic/tk.h:76:23: [B]fatal error: X11/Xlib.h: No such file or directory
compilation terminated.
make: *** [tk3d.o] Error 1
tk8.5.10 make failed! Exiting ...[/B]


one more thing is that while doing 'sudo apt-get update' it gives me the failure installing packages of X because of unreachable site, it gives me **Err [http://linux.ntuoss.org](http://linux.ntuoss.org) precise/universe amd64 Packages**

@dodo3773! may be what you suggested is the right place from where i can get **amd** updation, but i really have no idea about how to do it. need help :(


keeping in mind that m using 64bit machine.

---

### Post by dodo3773 on 2012-09-13
Go into your package manager to install the packages you need. Should be called "Software Center" or something similar. Search for it.

---

### Post by shallu on 2013-02-26
hi tried installing ns-2 2.35 in ubuntu 12.04 n i got the following error..

Kindly help me ....

TR_T=1 -DHAVE_UINTPTR_T=1 -DHAVE_SIGNED_CHAR=1 -DHAVE_LANGINFO=1 -DHAVE_SYS_IOCTL_H=1 -DTCL_UNLOAD_DLLS=1       /home/msit123/ns-allinone-2.35/tcl8.5.10/unix/../unix/tclAppInit.c
gcc -O2  -pipe    -Wl,--export-dynamic  tclAppInit.o -L/home/msit123/ns-allinone-2.35/tcl8.5.10/unix -ltcl8.5 -ldl  -lieee -lm  \
        -Wl,-rpath,/home/msit123/ns-allinone-2.35/lib -o tclsh
tcl8.5.10 make succeeded.
Installing libtcl8.5.a to /home/msit123/ns-allinone-2.35/lib/
cp: cannot create regular file `/home/msit123/ns-allinone-2.35/lib/#inst.14705#': Permission denied
rm: cannot remove `/home/msit123/ns-allinone-2.35/lib/libtcl8.5.a': Permission denied
mv: cannot stat `/home/msit123/ns-allinone-2.35/lib/#inst.14705#': No such file or directory
ranlib: could not create temporary file whilst writing archive: No more archived files
make: *** [install-binaries] Error 1
tcl8.5.10 installation failed.
Tcl is not part of the ns project.  Please see [www.Scriptics.com](www.Scriptics.com)
to see if they have a fix for your platform.
msit123@msit123-Studio-1435:~/ns-allinone-2.35$

---

### Post by schragge on 2013-02-26
Check the file permissions and the ownership.
```

namei -l /home/msit123/ns-allinone-2.35/lib

```

[highlight]PS.[/highlight]
Please start your own thread. Your problem has nothing to do with that of the OP.

---

