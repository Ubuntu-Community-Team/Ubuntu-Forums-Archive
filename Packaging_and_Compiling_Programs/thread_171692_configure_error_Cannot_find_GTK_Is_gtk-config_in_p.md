---
title: "configure: error: Cannot find GTK: Is gtk-config in path?"
date: 2006-05-07
forum: Packaging and Compiling Programs
---

### Post by 03swalker on 2006-05-07
Hi,
Whenever I try to install programs from source I get the following error:
"configure: error: Cannot find GTK: Is gtk-config in path?"
What the terminal says is pasted below, yet as I am new I have no idea what most of this means. Does anyone have any ideas what I need to do?


samuel@gamesgalore:~/Desktop/simplecdrx-1.3.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/samuel/Desktop/simplecdrx-1.3.3/missing: Unknown `--run' option
Try `/home/samuel/Desktop/simplecdrx-1.3.3/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
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
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
checking for Ogg... no
*** Could not run Ogg test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means Ogg was incorrectly installed
*** or that you have moved Ogg since it was installed.
checking for Vorbis... no
*** Could not run Vorbis test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means Vorbis was incorrectly installed
*** or that you have moved Vorbis since it was installed.
checking dependency style of gcc... (cached) gcc3
checking dependency style of g++... (cached) gcc3
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ranlib... ranlib
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... 4294967295U
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... yes
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for dup2... yes
checking for memset... yes
checking for mkdir... yes
checking for strerror... yes
checking for an ANSI C-conforming const... (cached) yes
checking for off_t... (cached) yes
checking for pid_t... yes
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?

---

### Post by Peter76 on 2006-05-07
You have to install libgtk-dev from Synaptic. There are also errors about libogg and libvorbis missing; install libogg-dev and libvorbis-dev.
Most of the time you get errors about missing libraries, you don't have the dev-files installed.

Good luck

---

### Post by 03swalker on 2006-05-07
Thanks for the quick reply, but the closest match to 'libgtk-dev' is 'libgtk2.0-dev' in my Synaptic. I have all repositories enabled, but if I try to install 'libgtk2.0-dev' i get errors saying
'Depends: libglib2.0-dev (>=2.7.1) but it is not installable
 Depends: libpango1.0-dev (>=1.10.0-2) but it is not installable
 Depends: libatk1.0-dev (>=1.6.1-2) but it is not installable
 Depends: libcairo2-dev but it is not going to be installed
 Depends: libx11-dev  but it is not installable or
 	xlibs-dev but it is not going to be installed
 Depends: libxext-dev  but it is not installable or
 	xlibs-dev but it is not going to be installed
 Depends: libxinerama-dev  but it is not installable
 Depends: libxi-dev  but it is not installable
 Depends: libxrandr-dev  but it is not installable
 Depends: libxcursor-dev  but it is not installable
 Depends: libxfixes-dev  but it is not installable'

Also 'libogg-dev' and 'libvorbis-dev' aren't listed.

Any help would be great. Thanks guys.

---

