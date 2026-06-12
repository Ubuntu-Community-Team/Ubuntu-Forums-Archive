---
title: "Source Code Compiling Error - VLC"
date: 2012-08-19
forum: Packaging and Compiling Programs
---

### Post by Yuva Raj on 2012-08-19
```


yuva@yuva-desktop:~/Downloads/vlc-2.0.3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for egrep... (cached) /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking dependency style of gcc -std=gnu99... gcc3
checking for desktop-file-validate... desktop-file-validate
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for 3rd party libraries path... not found
checking for an Android system... no
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for windres... no
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking whether nanosleep is declared... yes
checking for daemon... yes
checking for fcntl... yes
checking for fstatvfs... yes
checking for fork... yes
checking for getenv... yes
checking for getpwuid_r... yes
checking for if_nameindex... yes
checking for if_nametoindex... yes
checking for isatty... yes
checking for lstat... yes
checking for memalign... yes
checking for mmap... yes
checking for openat... yes
checking for pread... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for setlocale... yes
checking for stricmp... no
checking for strnicmp... no
checking for strptime... yes
checking for uselocale... yes
checking for atof... yes
checking for atoll... yes
checking for dirfd... yes
checking for fdopendir... yes
checking for flockfile... yes
checking for fsync... yes
checking for getdelim... yes
checking for getpid... yes
checking for gmtime_r... yes
checking for inet_pton... yes
checking for lldiv... yes
checking for localtime_r... yes
checking for nrand48... yes
checking for rewind... yes
checking for setenv... yes
checking for strcasecmp... yes
checking for strcasestr... yes
checking for strdup... yes
checking for strlcpy... no
checking for strncasecmp... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtof... yes
checking for strtok_r... yes
checking for strtoll... yes
checking for swab... yes
checking for tdestroy... yes
checking for fdatasync... yes
checking for working strcoll... yes
checking for accept4... yes
checking for pipe2... yes
checking for eventfd... yes
checking for vmsplice... yes
checking for sched_getaffinity... yes
checking for library containing poll... none required
checking for struct pollfd... yes
checking for library containing connect... none required
checking for socklen_t in sys/socket.h... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for getopt_long... yes
checking for cos in -lm... yes
checking for lrintf in -lm... yes
checking for library containing dlopen... -ldl
checking for main in -lpthread... yes
checking for clock_nanosleep in -lrt... yes
checking for strncasecmp in strings.h... yes
checking search.h usability... yes
checking search.h presence... yes
checking for search.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/udplite.h usability... no
checking netinet/udplite.h presence... no
checking for netinet/udplite.h... no
checking sys/eventfd.h usability... yes
checking sys/eventfd.h presence... yes
checking for sys/eventfd.h... yes
checking for net/if.h... yes
checking for sys/mount.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking linux/magic.h usability... yes
checking linux/magic.h presence... yes
checking for linux/magic.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking for ssize_t... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for DBUS... no
configure: error: No package 'dbus-1' found.



```

how to resolve this error?

---

### Post by SevenMachines on 2012-08-19
When you see this in a configure stage
```
configure: error: No package 'dbus-1' found.

```
it usually means you're missing the development package (those ending with -dev)
in this case
```
$ apt-cache search -n dbus-1 | grep dev
libdbus-1-dev - simple interprocess messaging system (development headers)

```
So 
```
$ sudo apt-get install libdbus-1-dev 

```and try again

To install all the build dependencies for ubuntu's version of a package then

```
$ sudo apt-get build-dep vlc

```

---

### Post by andrew.46 on 2012-11-24
vlc is a reasonably difficult one to compile. Have a look here to see one way of accomplishing this:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

Bear in mind that this guide is aimed at compiling and packaging the development version of vlc but the underlying principles remain true for the release versions. BTW 2.0.4 is out now :).

---

