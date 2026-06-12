---
title: "Setting up a MinGW enviroment"
date: 2010-06-08
forum: Programming Talk
---

### Post by blippy on 2010-06-08
I am trying to compile UNIXy programs on Windows 7 using MinGW. The problem is, I keep getting "can't lstat conftest.exe: Permission Denied". After Googling around, it seems that this often occurs on Windows 7. It looks like one of those handy Microsoft features that we've all come to adore.

So basically, MinGW on Win7 isn't going to work adequately. My big plan now is to use mingw on Ubuntu to cross-compile, because I want Windows native executables. I have installed mingw and wine on Ubuntu, but it is not obvious how I can just type "configure" and have it pick up the mingw compiler, libraries, and general environment. Is there a "sandbox"/shell that I can use?

---

### Post by Bachstelze on 2010-06-08
```
./configure --host=i586-mingw32msvc
```

It's as simple as this :)

```
firas@tsukino hello-2.4 % ./configure --host=i586-mingw32msvc
configure: WARNING: If you wanted to set the --build type, don't use --host.
    If a cross compiler is detected then cross compile mode will be used.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for i586-mingw32msvc-strip... i586-mingw32msvc-strip
checking for i586-mingw32msvc-gcc... i586-mingw32msvc-gcc
checking for C compiler default output file name... a.exe
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... .exe
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether i586-mingw32msvc-gcc accepts -g... yes
checking for i586-mingw32msvc-gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of i586-mingw32msvc-gcc... gcc3
checking for i586-mingw32msvc-ranlib... i586-mingw32msvc-ranlib
checking how to run the C preprocessor... i586-mingw32msvc-gcc -E
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
checking whether the preprocessor supports include_next... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... i586-pc-mingw32msvc
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking stdio_ext.h usability... no
checking stdio_ext.h presence... no
checking for stdio_ext.h... no
checking for stdlib.h... (cached) yes
checking sys/socket.h usability... no
checking sys/socket.h presence... no
checking for sys/socket.h... no
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking wctype.h usability... yes
checking wctype.h presence... yes
checking for wctype.h... yes
checking for complete errno.h... no
checking for EMULTIHOP value... no
checking for ENOLINK value... no
checking for EOVERFLOW value... no
checking whether strerror_r is declared... no
checking for strerror_r... no
checking whether strerror_r returns char *... no
checking for __fpending... no
checking for mbsinit... yes
checking for iswcntrl... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for getopt_long_only... yes
checking whether optreset is declared... no
checking for working GNU getopt function... yes
checking whether getenv is declared... yes
checking for inline... inline
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking whether strerror is declared... yes
checking winsock2.h usability... yes
checking winsock2.h presence... yes
checking for winsock2.h... yes
checking for C/C++ restrict keyword... __restrict
checking for wint_t... yes
checking for error_at_line... no
checking whether __fpending is declared... no
checking how to determine the number of pending output bytes on a stream... fp->_ptr - fp->_base
checking whether the compiler generally respects inline... yes
checking for mbstate_t... yes
checking whether mbrtowc and mbstate_t are properly declared... yes
checking for struct random_data... no
checking whether <wchar.h> is standalone... yes
checking whether iswcntrl works... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /usr/i586-mingw32msvc/bin/ld
checking if the linker (/usr/i586-mingw32msvc/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... no
checking for iconv... no, consider installing GNU libiconv
checking for GNU gettext in libintl... no
checking whether to use NLS... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating contrib/Makefile
config.status: creating doc/Makefile
config.status: creating gnulib/lib/Makefile
config.status: creating man/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
firas@tsukino hello-2.4 % make
 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating contrib/Makefile
config.status: creating doc/Makefile
config.status: creating gnulib/lib/Makefile
config.status: creating man/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
make  all-recursive
make[1]: Entering directory `/home/firas/software/hello-2.4'
Making all in contrib
make[2]: Entering directory `/home/firas/software/hello-2.4/contrib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/firas/software/hello-2.4/contrib'
Making all in gnulib/lib
make[2]: Entering directory `/home/firas/software/hello-2.4/gnulib/lib'
rm -f errno.h-t errno.h
{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */' && \
	  sed -e 's|@''INCLUDE_NEXT''@|include_next|g' \
	      -e 's|@''PRAGMA_SYSTEM_HEADER''@|#pragma GCC system_header|g' \
	      -e 's|@''NEXT_ERRNO_H''@|<errno.h>|g' \
	      -e 's|@''EMULTIHOP_HIDDEN''@|0|g' \
	      -e 's|@''EMULTIHOP_VALUE''@||g' \
	      -e 's|@''ENOLINK_HIDDEN''@|0|g' \
	      -e 's|@''ENOLINK_VALUE''@||g' \
	      -e 's|@''EOVERFLOW_HIDDEN''@|0|g' \
	      -e 's|@''EOVERFLOW_VALUE''@||g' \
	      < ./errno.in.h; \
	} > errno.h-t
mv errno.h-t errno.h
rm -f stdlib.h-t stdlib.h
{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */' && \
	  sed -e 's|@''INCLUDE_NEXT''@|include_next|g' \
	      -e 's|@''PRAGMA_SYSTEM_HEADER''@|#pragma GCC system_header|g' \
	      -e 's|@''NEXT_STDLIB_H''@|<stdlib.h>|g' \
	      -e 's|@''GNULIB_MALLOC_POSIX''@|0|g' \
	      -e 's|@''GNULIB_REALLOC_POSIX''@|0|g' \
	      -e 's|@''GNULIB_CALLOC_POSIX''@|0|g' \
	      -e 's|@''GNULIB_ATOLL''@|0|g' \
	      -e 's|@''GNULIB_GETLOADAVG''@|0|g' \
	      -e 's|@''GNULIB_GETSUBOPT''@|0|g' \
	      -e 's|@''GNULIB_MKDTEMP''@|0|g' \
	      -e 's|@''GNULIB_MKSTEMP''@|0|g' \
	      -e 's|@''GNULIB_PUTENV''@|0|g' \
	      -e 's|@''GNULIB_RANDOM_R''@|0|g' \
	      -e 's|@''GNULIB_RPMATCH''@|0|g' \
	      -e 's|@''GNULIB_SETENV''@|0|g' \
	      -e 's|@''GNULIB_STRTOD''@|0|g' \
	      -e 's|@''GNULIB_STRTOLL''@|0|g' \
	      -e 's|@''GNULIB_STRTOULL''@|0|g' \
	      -e 's|@''GNULIB_UNSETENV''@|0|g' \
	      -e 's|@''HAVE_ATOLL''@|1|g' \
	      -e 's|@''HAVE_CALLOC_POSIX''@|1|g' \
	      -e 's|@''HAVE_GETSUBOPT''@|1|g' \
	      -e 's|@''HAVE_MALLOC_POSIX''@|1|g' \
	      -e 's|@''HAVE_MKDTEMP''@|1|g' \
	      -e 's|@''HAVE_REALLOC_POSIX''@|1|g' \
	      -e 's|@''HAVE_RANDOM_R''@|1|g' \
	      -e 's|@''HAVE_RPMATCH''@|1|g' \
	      -e 's|@''HAVE_SETENV''@|1|g' \
	      -e 's|@''HAVE_STRTOD''@|1|g' \
	      -e 's|@''HAVE_STRTOLL''@|1|g' \
	      -e 's|@''HAVE_STRTOULL''@|1|g' \
	      -e 's|@''HAVE_STRUCT_RANDOM_DATA''@|0|g' \
	      -e 's|@''HAVE_SYS_LOADAVG_H''@|0|g' \
	      -e 's|@''HAVE_UNSETENV''@|1|g' \
	      -e 's|@''HAVE_DECL_GETLOADAVG''@|1|g' \
	      -e 's|@''REPLACE_MKSTEMP''@|0|g' \
	      -e 's|@''REPLACE_PUTENV''@|0|g' \
	      -e 's|@''REPLACE_STRTOD''@|0|g' \
	      -e 's|@''VOID_UNSETENV''@|0|g' \
	      -e '/definition of GL_LINK_WARNING/r ../../build-aux/link-warning.h' \
	      < ./stdlib.in.h; \
	} > stdlib.h-t
mv stdlib.h-t stdlib.h
rm -f string.h-t string.h
{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */' && \
	  sed -e 's|@''INCLUDE_NEXT''@|include_next|g' \
	      -e 's|@''PRAGMA_SYSTEM_HEADER''@|#pragma GCC system_header|g' \
	      -e 's|@''NEXT_STRING_H''@|<string.h>|g' \
	      -e 's|@''GNULIB_MBSLEN''@|0|g' \
	      -e 's|@''GNULIB_MBSNLEN''@|0|g' \
	      -e 's|@''GNULIB_MBSCHR''@|0|g' \
	      -e 's|@''GNULIB_MBSRCHR''@|0|g' \
	      -e 's|@''GNULIB_MBSSTR''@|0|g' \
	      -e 's|@''GNULIB_MBSCASECMP''@|0|g' \
	      -e 's|@''GNULIB_MBSNCASECMP''@|0|g' \
	      -e 's|@''GNULIB_MBSPCASECMP''@|0|g' \
	      -e 's|@''GNULIB_MBSCASESTR''@|0|g' \
	      -e 's|@''GNULIB_MBSCSPN''@|0|g' \
	      -e 's|@''GNULIB_MBSPBRK''@|0|g' \
	      -e 's|@''GNULIB_MBSSPN''@|0|g' \
	      -e 's|@''GNULIB_MBSSEP''@|0|g' \
	      -e 's|@''GNULIB_MBSTOK_R''@|0|g' \
	      -e 's|@''GNULIB_MEMMEM''@|0|g' \
	      -e 's|@''GNULIB_MEMPCPY''@|0|g' \
	      -e 's|@''GNULIB_MEMRCHR''@|0|g' \
	      -e 's|@''GNULIB_RAWMEMCHR''@|0|g' \
	      -e 's|@''GNULIB_STPCPY''@|0|g' \
	      -e 's|@''GNULIB_STPNCPY''@|0|g' \
	      -e 's|@''GNULIB_STRCHRNUL''@|0|g' \
	      -e 's|@''GNULIB_STRDUP''@|0|g' \
	      -e 's|@''GNULIB_STRNDUP''@|0|g' \
	      -e 's|@''GNULIB_STRNLEN''@|0|g' \
	      -e 's|@''GNULIB_STRPBRK''@|0|g' \
	      -e 's|@''GNULIB_STRSEP''@|0|g' \
	      -e 's|@''GNULIB_STRSTR''@|0|g' \
	      -e 's|@''GNULIB_STRCASESTR''@|0|g' \
	      -e 's|@''GNULIB_STRTOK_R''@|0|g' \
	      -e 's|@''GNULIB_STRERROR''@|1|g' \
	      -e 's|@''GNULIB_STRSIGNAL''@|0|g' \
	      -e 's|@''GNULIB_STRVERSCMP''@|0|g' \
	      -e 's|@''HAVE_DECL_MEMMEM''@|1|g' \
	      -e 's|@''HAVE_MEMPCPY''@|1|g' \
	      -e 's|@''HAVE_DECL_MEMRCHR''@|1|g' \
	      -e 's|@''HAVE_RAWMEMCHR''@|1|g' \
	      -e 's|@''HAVE_STPCPY''@|1|g' \
	      -e 's|@''HAVE_STPNCPY''@|1|g' \
	      -e 's|@''HAVE_STRCHRNUL''@|1|g' \
	      -e 's|@''HAVE_DECL_STRDUP''@|1|g' \
	      -e 's|@''HAVE_STRNDUP''@|1|g' \
	      -e 's|@''HAVE_DECL_STRNDUP''@|1|g' \
	      -e 's|@''HAVE_DECL_STRNLEN''@|1|g' \
	      -e 's|@''HAVE_STRPBRK''@|1|g' \
	      -e 's|@''HAVE_STRSEP''@|1|g' \
	      -e 's|@''HAVE_STRCASESTR''@|1|g' \
	      -e 's|@''HAVE_DECL_STRTOK_R''@|1|g' \
	      -e 's|@''HAVE_DECL_STRERROR''@|1|g' \
	      -e 's|@''HAVE_DECL_STRSIGNAL''@|1|g' \
	      -e 's|@''HAVE_STRVERSCMP''@|1|g' \
	      -e 's|@''REPLACE_MEMMEM''@|0|g' \
	      -e 's|@''REPLACE_STRCASESTR''@|0|g' \
	      -e 's|@''REPLACE_STRDUP''@|0|g' \
	      -e 's|@''REPLACE_STRSTR''@|0|g' \
	      -e 's|@''REPLACE_STRERROR''@|1|g' \
	      -e 's|@''REPLACE_STRSIGNAL''@|0|g' \
	      -e '/definition of GL_LINK_WARNING/r ../../build-aux/link-warning.h' \
	      < ./string.in.h; \
	} > string.h-t
mv string.h-t string.h
rm -f unistd.h-t unistd.h
{ echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */'; \
	  sed -e 's|@''HAVE_UNISTD_H''@|1|g' \
	      -e 's|@''INCLUDE_NEXT''@|include_next|g' \
	      -e 's|@''PRAGMA_SYSTEM_HEADER''@|#pragma GCC system_header|g' \
	      -e 's|@''NEXT_UNISTD_H''@|<unistd.h>|g' \
	      -e 's|@''GNULIB_CHOWN''@|0|g' \
	      -e 's|@''GNULIB_CLOSE''@|0|g' \
	      -e 's|@''GNULIB_DUP2''@|0|g' \
	      -e 's|@''GNULIB_ENVIRON''@|0|g' \
	      -e 's|@''GNULIB_EUIDACCESS''@|0|g' \
	      -e 's|@''GNULIB_FCHDIR''@|0|g' \
	      -e 's|@''GNULIB_FSYNC''@|0|g' \
	      -e 's|@''GNULIB_FTRUNCATE''@|0|g' \
	      -e 's|@''GNULIB_GETCWD''@|0|g' \
	      -e 's|@''GNULIB_GETDOMAINNAME''@|0|g' \
	      -e 's|@''GNULIB_GETDTABLESIZE''@|0|g' \
	      -e 's|@''GNULIB_GETHOSTNAME''@|0|g' \
	      -e 's|@''GNULIB_GETLOGIN_R''@|0|g' \
	      -e 's|@''GNULIB_GETPAGESIZE''@|0|g' \
	      -e 's|@''GNULIB_GETUSERSHELL''@|0|g' \
	      -e 's|@''GNULIB_LCHOWN''@|0|g' \
	      -e 's|@''GNULIB_LSEEK''@|0|g' \
	      -e 's|@''GNULIB_READLINK''@|0|g' \
	      -e 's|@''GNULIB_SLEEP''@|0|g' \
	      -e 's|@''GNULIB_UNISTD_H_SIGPIPE''@|0|g' \
	      -e 's|@''GNULIB_WRITE''@|0|g' \
	      -e 's|@''HAVE_DUP2''@|1|g' \
	      -e 's|@''HAVE_EUIDACCESS''@|1|g' \
	      -e 's|@''HAVE_FSYNC''@|1|g' \
	      -e 's|@''HAVE_FTRUNCATE''@|1|g' \
	      -e 's|@''HAVE_GETDOMAINNAME''@|1|g' \
	      -e 's|@''HAVE_GETDTABLESIZE''@|1|g' \
	      -e 's|@''HAVE_GETHOSTNAME''@|1|g' \
	      -e 's|@''HAVE_GETPAGESIZE''@|1|g' \
	      -e 's|@''HAVE_GETUSERSHELL''@|1|g' \
	      -e 's|@''HAVE_READLINK''@|1|g' \
	      -e 's|@''HAVE_SLEEP''@|1|g' \
	      -e 's|@''HAVE_DECL_ENVIRON''@|1|g' \
	      -e 's|@''HAVE_DECL_GETLOGIN_R''@|1|g' \
	      -e 's|@''HAVE_OS_H''@|0|g' \
	      -e 's|@''HAVE_SYS_PARAM_H''@|0|g' \
	      -e 's|@''REPLACE_CHOWN''@|0|g' \
	      -e 's|@''REPLACE_CLOSE''@|0|g' \
	      -e 's|@''REPLACE_FCHDIR''@|0|g' \
	      -e 's|@''REPLACE_GETCWD''@|0|g' \
	      -e 's|@''REPLACE_GETPAGESIZE''@|0|g' \
	      -e 's|@''REPLACE_LCHOWN''@|0|g' \
	      -e 's|@''REPLACE_LSEEK''@|0|g' \
	      -e 's|@''REPLACE_WRITE''@|0|g' \
	      -e 's|@''UNISTD_H_HAVE_WINSOCK2_H''@|0|g' \
	      -e '/definition of GL_LINK_WARNING/r ../../build-aux/link-warning.h' \
	      < ./unistd.in.h; \
	} > unistd.h-t
mv unistd.h-t unistd.h
make  all-recursive
make[3]: Entering directory `/home/firas/software/hello-2.4/gnulib/lib'
make[4]: Entering directory `/home/firas/software/hello-2.4/gnulib/lib'
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT xalloc-die.o -MD -MP -MF .deps/xalloc-die.Tpo -c -o xalloc-die.o xalloc-die.c
mv -f .deps/xalloc-die.Tpo .deps/xalloc-die.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT close-stream.o -MD -MP -MF .deps/close-stream.Tpo -c -o close-stream.o close-stream.c
mv -f .deps/close-stream.Tpo .deps/close-stream.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT closeout.o -MD -MP -MF .deps/closeout.Tpo -c -o closeout.o closeout.c
mv -f .deps/closeout.Tpo .deps/closeout.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT error.o -MD -MP -MF .deps/error.Tpo -c -o error.o error.c
mv -f .deps/error.Tpo .deps/error.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT exitfail.o -MD -MP -MF .deps/exitfail.Tpo -c -o exitfail.o exitfail.c
mv -f .deps/exitfail.Tpo .deps/exitfail.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT fpending.o -MD -MP -MF .deps/fpending.Tpo -c -o fpending.o fpending.c
mv -f .deps/fpending.Tpo .deps/fpending.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT quotearg.o -MD -MP -MF .deps/quotearg.Tpo -c -o quotearg.o quotearg.c
mv -f .deps/quotearg.Tpo .deps/quotearg.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT strerror.o -MD -MP -MF .deps/strerror.Tpo -c -o strerror.o strerror.c
mv -f .deps/strerror.Tpo .deps/strerror.Po
i586-mingw32msvc-gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -g -O2 -MT xmalloc.o -MD -MP -MF .deps/xmalloc.Tpo -c -o xmalloc.o xmalloc.c
mv -f .deps/xmalloc.Tpo .deps/xmalloc.Po
rm -f libgnu.a
ar cru libgnu.a xalloc-die.o close-stream.o closeout.o error.o exitfail.o fpending.o quotearg.o strerror.o xmalloc.o
i586-mingw32msvc-ranlib libgnu.a
make[4]: Leaving directory `/home/firas/software/hello-2.4/gnulib/lib'
make[3]: Leaving directory `/home/firas/software/hello-2.4/gnulib/lib'
make[2]: Leaving directory `/home/firas/software/hello-2.4/gnulib/lib'
Making all in po
make[2]: Entering directory `/home/firas/software/hello-2.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/firas/software/hello-2.4/po'
Making all in src
make[2]: Entering directory `/home/firas/software/hello-2.4/src'
i586-mingw32msvc-gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I..  -I../gnulib/lib -I../gnulib/lib   -g -O2 -MT hello.o -MD -MP -MF .deps/hello.Tpo -c -o hello.o hello.c
mv -f .deps/hello.Tpo .deps/hello.Po
i586-mingw32msvc-gcc  -g -O2   -o hello.exe hello.o ../gnulib/lib/libgnu.a 
make[2]: Leaving directory `/home/firas/software/hello-2.4/src'
Making all in doc
make[2]: Entering directory `/home/firas/software/hello-2.4/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/firas/software/hello-2.4/doc'
Making all in man
make[2]: Entering directory `/home/firas/software/hello-2.4/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/firas/software/hello-2.4/man'
Making all in tests
make[2]: Entering directory `/home/firas/software/hello-2.4/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/firas/software/hello-2.4/tests'
make[2]: Entering directory `/home/firas/software/hello-2.4'
make[2]: Leaving directory `/home/firas/software/hello-2.4'
make[1]: Leaving directory `/home/firas/software/hello-2.4'
firas@tsukino hello-2.4 % file src/hello.exe 
src/hello.exe: PE32 executable for MS Windows (console) Intel 80386 32-bit
firas@tsukino hello-2.4 % wine src/hello.exe 
Hello, world!
firas@tsukino hello-2.4 %
```

---

### Post by mmix on 2010-06-08
On windows 7, try this:

1 or 2 or combo.

1. uac
2. dep

[http://www.mydigitallife.info/2008/12/30/how-to-disable-and-turn-off-uac-in-windows-7/](http://www.mydigitallife.info/2008/12/30/how-to-disable-and-turn-off-uac-in-windows-7/)

[http://www.itechtalk.com/thread3591.html](http://www.itechtalk.com/thread3591.html)

---

