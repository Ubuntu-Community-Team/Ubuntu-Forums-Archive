---
title: "make fails while trying to compile glibc-2.2.5"
date: 2010-01-09
forum: Packaging and Compiling Programs
---

### Post by drs86 on 2010-01-09
Hi,

I'm trying to compile glibc-2.2.5 with Karmic. (I need the old library because I've got an old version of MATLAB that doesn't like the newer libraries. I'm not trying to install the old library system-wide; I was just going to try to drop it into the MATLAB library space.) My setup includes the following:

Linux kernel 2.6.31
libc6
gcc 4.4.1
make 3.81
sed 4.2.1
mawk 1.3.3

I got the configure script to run successfully (after I modified the script to make it accept my version of gcc). Here's the output of configure:
```
david@drs-toshiba-koalaVM:~/Applications/glibc-2.2.5$ ./configure --prefix=/home/david/Applications/glibc-build --enable-add-ons=linuxthreadsloading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking sysdep dirs... sysdeps/i386/elf linuxthreads/sysdeps/unix/sysv/linux/i386 linuxthreads/sysdeps/unix/sysv/linux linuxthreads/sysdeps/pthread sysdeps/pthread linuxthreads/sysdeps/unix/sysv linuxthreads/sysdeps/unix linuxthreads/sysdeps/i386/i686 linuxthreads/sysdeps/i386 sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 sysdeps/unix/sysv sysdeps/unix/i386 sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686 sysdeps/i386/i486 sysdeps/i386/fpu sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for pwd... (cached) /bin/pwd
checking build system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking version of gcc... 4.4.1, ok
checking for gnumake... (cached) make
checking version of make... 3.81, ok
checking for gnumsgfmt... (cached) msgfmt
checking version of msgfmt... 0.17, ok
checking for makeinfo... (cached) makeinfo
checking version of makeinfo... 4.13, ok
checking for gsed... (cached) sed
checking version of sed... 4.2.1, ok
checking whether the C compiler (gcc  ) works... (cached) yes
checking whether the C compiler (gcc  ) is a cross-compiler... (cached) no
checking whether we are using GNU C... (cached) yes
checking build system type... i686-pc-linux-gnu
checking how to run the C preprocessor... (cached) gcc -E
checking for ranlib... (cached) ranlib
checking whether as is GNU as... (cached) yes
checking whether ld is GNU ld... (cached) yes
checking for mig... (cached) mig
checking whether ranlib is necessary... (cached) no
checking LD_LIBRARY_PATH variable... ok
checking whether GCC supports -static-libgcc... (cached) -static-libgcc
checking for bash... (cached) /bin/bash
checking for mawk... (cached) mawk
checking for perl... (cached) /usr/bin/perl
checking for install-info... (cached) /usr/sbin/install-info
checking for old Debian install-info... (cached) no
checking for bison... (cached) no
checking for signed size_t type... (cached) no
checking for libc-friendly stddef.h... (cached) yes
checking whether we need to use -P to assemble .S files... (cached) no
checking whether .text pseudo-op must be used... (cached) yes
checking for assembler global-symbol directive... (cached) .globl
checking for .set assembler directive... (cached) yes
checking for .symver assembler directive... (cached) yes
checking for ld --version-script... (cached) yes
checking for .previous assembler directive... (cached) yes
checking for .protected and .hidden assembler directive... (cached) yes
checking for -z nodelete option... (cached) yes
checking for -z nodlopen option... (cached) yes
checking for -z initfirst option... (cached) yes
checking for -Bgroup option... (cached) yes
checking for -z combreloc... (cached) yes
checking whether cc puts quotes around section names... (cached) no
checking for assembler .weak directive... (cached) yes
checking for ld --no-whole-archive... (cached) yes
checking for gcc -fexceptions... (cached) yes
checking for DWARF2 unwind info support... (cached) no
checking for __builtin_expect... (cached) yes
checking for local label subtraction... (cached) yes
checking for libgd... no
checking size of long double... (cached) 12
running configure fragment for ./linuxthreads/sysdeps/unix/sysv/linux
running configure fragment for ./sysdeps/unix/sysv/linux
checking installed Linux kernel header files... (cached) 2.0.10 or later
checking for symlinks in /home/david/Applications/glibc-build/include... ok
running configure fragment for ./sysdeps/unix/common
running configure fragment for ./sysdeps/unix
running configure fragment for ./sysdeps/generic
checking stdio selection... libio
checking for old glibc 2.0.x headers... no
checking whether -fPIC is default... no
creating ./config.status
creating config.make
creating glibcbug
creating config.h
config.h is unchanged
configuring in linuxthreads
running /bin/sh ./configure  --prefix=/home/david/Applications/glibc-build --enable-add-ons=linuxthreads --cache-file=.././config.cache --srcdir=.
```But then when I ran make, it gave me errors:
```
david@drs-toshiba-koalaVM:~/Applications/glibc-2.2.5$ make
cat shlib-versions linuxthreads/shlib-versions linuxthreads_db/shlib-versions \
    | sed '/^[     ]*#/d;s/^[     ]*%/#/' | gcc -E -undef -I. -Iinclude -include sysdeps/../config.h -DASSEMBLER -x assembler-with-cpp - | sed '/^[     ]*#/d;/^[     ]*$/d' \
    | while read conf version setname; do \
        test -n "$version" && \
        test `expr 'i686-pc-linux-gnu' \
               : "$conf"` != 0 || continue; \
        if test "x$version" = xDEFAULT; then \
          default_setname="$setname"; \
        else \
          lib=`echo $version | sed 's/=.*$//'`; \
          if eval test -z "\${versioned_${lib}}"; then \
        eval versioned_${lib}=yes; \
        number=`echo $version | sed "s/^.*=//"`; \
        echo $lib $number ${setname:-${default_setname}}; \
          fi; \
        fi; \
      done > sysdeps/../soversions.iT; exit 0
mv -f sysdeps/../soversions.iT sysdeps/../soversions.i
{ while read lib version setname; do \
        test -z "$setname" || echo "$lib : $setname"; \
      done < sysdeps/../soversions.i; \
      cat Versions.def \
      | sed '/^[     ]*#/d;s/^[     ]*%/#/' | gcc -E -undef -I. -Iinclude -include sysdeps/../config.h -DASSEMBLER -x assembler-with-cpp - | sed '/^[     ]*#/d;/^[     ]*$/d'; \
    } | LC_ALL=C mawk -f scripts/firstversions.awk > sysdeps/../Versions.allT
mv -f sysdeps/../Versions.allT sysdeps/../Versions.all
( echo 'sysd-versions-subdirs = csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow po argp crypt linuxthreads nss localedata timezone rt conform debug linuxthreads_db inet resolv hesiod sunrpc nis nscd streams login dlfcn elf sysdeps/i386/elf linuxthreads/sysdeps/unix/sysv/linux/i386 linuxthreads/sysdeps/unix/sysv/linux linuxthreads/sysdeps/pthread sysdeps/pthread linuxthreads/sysdeps/unix/sysv linuxthreads/sysdeps/unix linuxthreads/sysdeps/i386/i686 linuxthreads/sysdeps/i386 sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 sysdeps/unix/sysv sysdeps/unix/i386 sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686 sysdeps/i386/i486 sysdeps/i386/fpu sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic' ; \
      cat csu/Versions assert/Versions ctype/Versions locale/Versions intl/Versions catgets/Versions math/Versions setjmp/Versions signal/Versions stdlib/Versions stdio-common/Versions libio/Versions malloc/Versions string/Versions wcsmbs/Versions time/Versions dirent/Versions grp/Versions pwd/Versions posix/Versions io/Versions termios/Versions resource/Versions misc/Versions socket/Versions sysvipc/Versions gmon/Versions iconv/Versions wctype/Versions shadow/Versions argp/Versions crypt/Versions linuxthreads/Versions nss/Versions rt/Versions debug/Versions linuxthreads_db/Versions inet/Versions resolv/Versions hesiod/Versions sunrpc/Versions nis/Versions streams/Versions login/Versions dlfcn/Versions elf/Versions linuxthreads/sysdeps/i386/i686/Versions sysdeps/unix/sysv/linux/i386/Versions sysdeps/unix/sysv/linux/Versions sysdeps/unix/sysv/Versions sysdeps/i386/i686/Versions sysdeps/i386/i486/Versions sysdeps/i386/fpu/Versions sysdeps/i386/Versions \
      | sed '/^[     ]*#/d;s/^[     ]*%/#/' | gcc -E -undef -I. -Iinclude -include sysdeps/../config.h -DASSEMBLER -x assembler-with-cpp - | sed '/^[     ]*#/d;/^[     ]*$/d' \
      | LC_ALL=C mawk -v buildroot=sysdeps/../ -v defsfile=sysdeps/../Versions.all \
                -v move_if_change='/bin/sh scripts/move-if-change' \
                -f scripts/versions.awk; \
    ) > sysdeps/../sysd-versionsT
sysdeps/../ld.map is unchanged
sysdeps/../libBrokenLocale.map is unchanged
sysdeps/../libanl.map is unchanged
sysdeps/../libc.map is unchanged
sysdeps/../libcrypt.map is unchanged
sysdeps/../libdl.map is unchanged
sysdeps/../libm.map is unchanged
sysdeps/../libnsl.map is unchanged
sysdeps/../libnss_compat.map is unchanged
sysdeps/../libnss_dns.map is unchanged
sysdeps/../libnss_files.map is unchanged
sysdeps/../libnss_hesiod.map is unchanged
sysdeps/../libnss_nis.map is unchanged
sysdeps/../libnss_nisplus.map is unchanged
sysdeps/../libpthread.map is unchanged
sysdeps/../libresolv.map is unchanged
sysdeps/../librt.map is unchanged
sysdeps/../libthread_db.map is unchanged
sysdeps/../libutil.map is unchanged
mv -f sysdeps/../sysd-versionsT sysdeps/../sysd-versions
(echo 'sysd-rules-sysdirs := sysdeps/i386/elf linuxthreads/sysdeps/unix/sysv/linux/i386 linuxthreads/sysdeps/unix/sysv/linux linuxthreads/sysdeps/pthread sysdeps/pthread linuxthreads/sysdeps/unix/sysv linuxthreads/sysdeps/unix linuxthreads/sysdeps/i386/i686 linuxthreads/sysdeps/i386 sysdeps/unix/sysv/linux/i386/i686 sysdeps/unix/sysv/linux/i386 sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv/i386 sysdeps/unix/sysv sysdeps/unix/i386 sysdeps/unix sysdeps/posix sysdeps/i386/i686/fpu sysdeps/i386/i686 sysdeps/i386/i486 sysdeps/i386/fpu sysdeps/i386 sysdeps/wordsize-32 sysdeps/ieee754/ldbl-96 sysdeps/ieee754/dbl-64 sysdeps/ieee754/flt-32 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic';              \
     for dir in '$(..)sysdeps/i386/elf' '$(..)linuxthreads/sysdeps/unix/sysv/linux/i386' '$(..)linuxthreads/sysdeps/unix/sysv/linux' '$(..)linuxthreads/sysdeps/pthread' '$(..)sysdeps/pthread' '$(..)linuxthreads/sysdeps/unix/sysv' '$(..)linuxthreads/sysdeps/unix' '$(..)linuxthreads/sysdeps/i386/i686' '$(..)linuxthreads/sysdeps/i386' '$(..)sysdeps/unix/sysv/linux/i386/i686' '$(..)sysdeps/unix/sysv/linux/i386' '$(..)sysdeps/unix/sysv/linux' '$(..)sysdeps/gnu' '$(..)sysdeps/unix/common' '$(..)sysdeps/unix/mman' '$(..)sysdeps/unix/inet' '$(..)sysdeps/unix/sysv/i386' '$(..)sysdeps/unix/sysv' '$(..)sysdeps/unix/i386' '$(..)sysdeps/unix' '$(..)sysdeps/posix' '$(..)sysdeps/i386/i686/fpu' '$(..)sysdeps/i386/i686' '$(..)sysdeps/i386/i486' '$(..)sysdeps/i386/fpu' '$(..)sysdeps/i386' '$(..)sysdeps/wordsize-32' '$(..)sysdeps/ieee754/ldbl-96' '$(..)sysdeps/ieee754/dbl-64' '$(..)sysdeps/ieee754/flt-32' '$(..)sysdeps/ieee754' '$(..)sysdeps/generic/elf' '$(..)sysdeps/generic'; do                  \
       for o in .o .os .op .og .ob .oS; do \
          \
         echo "\$(objpfx)%$o: $dir/%.S \$(before-compile); \
          \$(compile-command.S)";                      \
         echo "\$(objpfx)%$o: $dir/%.s \$(before-compile); \
          \$(compile-command.s)";                      \
             \
         echo "\$(objpfx)%$o: $dir/%.c \$(before-compile); \
          \$(compile-command.c)";                      \
       done; \
        \
       echo "\$(objpfx)%.d: $dir/%.s \$(common-objpfx)dummy.d; \
        \$(make-dummy-dep)";                   \
       echo "\$(objpfx)%.d: $dir/%.S \$(before-compile); \
        \$(+make-deps)";                          \
           \
       echo "\$(objpfx)%.d: $dir/%.c \$(before-compile); \
        \$(+make-deps)";                          \
     done;                                      \
     echo 'sysd-rules-done = t') > sysdeps/../sysd-rulesT
mv -f sysdeps/../sysd-rulesT sysdeps/../sysd-rules
(while read lib number setname; do \
       case $number in \
         [0-9]*) echo "$lib.so-version=.$number"; \
             echo "all-sonames+=$lib=$lib.so\$($lib.so-version)";;\
         *)         echo "$lib.so-version=$number"; \
             echo "all-sonames+=$lib=\$($lib.so-version)";;\
       esac; \
     done; \
     echo soversions.mk-done = t;) < sysdeps/../soversions.i > sysdeps/../soversions.mkT; exit 0
mv -f sysdeps/../soversions.mkT sysdeps/../soversions.mk
mawk 'BEGIN { subdirs = ""; inhibit = "" };            \
        /^#/ { next };                        \
        /^[^-]/ { subdirs = subdirs " " $0 };            \
        /^-/ { inhibit = inhibit " " substr($0, 2) };        \
        END { printf "sysdep-subdirs =%s\n", subdirs;        \
              printf "sysdep-inhibit-subdirs =%s\n", inhibit;    \
              print "sysd-dirs-done = t" }'            \
           /dev/null linuxthreads/sysdeps/pthread/Subdirs sysdeps/unix/inet/Subdirs sysdeps/unix/Subdirs > sysdeps/../sysd-dirs-tmp
mv -f sysdeps/../sysd-dirs-tmp sysdeps/../sysd-dirs
{ { dirs='assert catgets iconvdata intl libio localedata malloc nis nscd nss posix resolv rt stdio-common string time wcsmbs';\
        for d in $dirs; do                          \
          while read on; do                          \
        echo "depend $d $on";                      \
          done < $d/Depend;                      \
        done;                              \
        for f in csu assert ctype locale intl catgets math setjmp signal stdlib stdio-common libio malloc string wcsmbs time dirent grp pwd posix io termios resource misc socket sysvipc gmon gnulib iconv iconvdata wctype manual shadow po argp crypt linuxthreads nss localedata timezone rt conform debug linuxthreads_db inet resolv hesiod sunrpc nis nscd streams login dlfcn elf; do                      \
          echo $f;                              \
        done;                              \
      } | mawk -f scripts/gen-sorted.awk &&                          \
      echo sysd-sorted-done = t;                      \
    } > sysdeps/../sysd-sorted-tmp
mv -f sysdeps/../sysd-sorted-tmp sysdeps/../sysd-sorted
make  -C csu subdir_lib
make[1]: Entering directory `/home/david/Applications/glibc-2.2.5/csu'
echo '#include "../posix/bits/posix1_lim.h"' |        \
    SUNPRO_DEPENDENCIES='../bits/stdio_lim.dT ../bits/stdio_lim.st'                \
    gcc -I../include -I.  -I.. -I../libio  -I../sysdeps/i386/elf -I../linuxthreads/sysdeps/unix/sysv/linux/i386 -I../linuxthreads/sysdeps/unix/sysv/linux -I../linuxthreads/sysdeps/pthread -I../sysdeps/pthread -I../linuxthreads/sysdeps/unix/sysv -I../linuxthreads/sysdeps/unix -I../linuxthreads/sysdeps/i386/i686 -I../linuxthreads/sysdeps/i386 -I../sysdeps/unix/sysv/linux/i386/i686 -I../sysdeps/unix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/inet -I../sysdeps/unix/sysv/i386 -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../sysdeps/i386/i686 -I../sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../sysdeps/i386 -I../sysdeps/wordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sysdeps/generic/elf -I../sysdeps/generic   -E -dM -xc - -o ../bits/stdio_lim.hT
echo '#include "../misc/sys/uio.h"' |                \
    SUNPRO_DEPENDENCIES='../bits/stdio_lim.dT ../bits/stdio_lim.st'                \
    gcc -D_LIBC=1 -I../include -I.  -I.. -I../libio  -I../sysdeps/i386/elf -I../linuxthreads/sysdeps/unix/sysv/linux/i386 -I../linuxthreads/sysdeps/unix/sysv/linux -I../linuxthreads/sysdeps/pthread -I../sysdeps/pthread -I../linuxthreads/sysdeps/unix/sysv -I../linuxthreads/sysdeps/unix -I../linuxthreads/sysdeps/i386/i686 -I../linuxthreads/sysdeps/i386 -I../sysdeps/unix/sysv/linux/i386/i686 -I../sysdeps/unix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/inet -I../sysdeps/unix/sysv/i386 -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../sysdeps/i386/i686 -I../sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../sysdeps/i386 -I../sysdeps/wordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sysdeps/generic/elf -I../sysdeps/generic   -E -dM -xc - | cat - >> ../bits/stdio_lim.hT
cat ../bits/stdio_lim.dT >> ../bits/stdio_lim.d
fopen_max=`sed -n 's/^#define OPEN_MAX //1p' ../bits/stdio_lim.hT`;     \
    filename_max=`sed -n 's/^#define PATH_MAX //1p' ../bits/stdio_lim.hT`;    \
    iov_max=`sed -n 's/^#define UIO_MAXIOV //p' ../bits/stdio_lim.hT`;    \
    fopen_max=${fopen_max:-16};                    \
    filename_max=${filename_max:-1024};                \
    if [ -z $iov_max ]; then                    \
      define_iov_max="# undef IOV_MAX";                \
    else                                \
      define_iov_max="# define IOV_MAX $iov_max";            \
    fi;                                \
    sed -e "s/@FOPEN_MAX@/$fopen_max/"                \
        -e "s/@FILENAME_MAX@/$filename_max/"            \
        -e "s/@L_tmpnam@/20/"                \
        -e "s/@TMP_MAX@/238328/"                \
        -e "s/@L_ctermid@/9/"                \
        -e "s/@L_cuserid@/9/"                \
        -e "s/@define_IOV_MAX@/$define_iov_max/"            \
        ../stdio-common/stdio_lim.h.in > ../bits/stdio_lim.h.new
/bin/sh ../scripts/move-if-change ../bits/stdio_lim.h.new ../bits/stdio_lim.h
../bits/stdio_lim.h is unchanged
rm -f ../bits/stdio_lim.hT ../bits/stdio_lim.dT ../bits/stdio_lim.dt
touch ../bits/stdio_lim.st
(case linux-gnu in \
       linux*) version=`(echo -e "#include <linux/version.h>\nUTS_RELEASE"\
                 | gcc -E -P - | \
                 sed -e 's/"\([^"]*\)".*/\1/p' -e d) 2>/dev/null`;\
           if [ -z "$version" ]; then \
             if [ -r /proc/version ]; then \
               version=`sed 's/.*Linux version \([^ ]*\) .*/>>\1<</' \
                < /proc/version`; \
             else \
               version=`uname -r`; \
             fi; \
           fi; \
           os=`uname -s 2> /dev/null`; \
           if [ -z "$os" ]; then \
             os=Linux; \
           fi; \
           echo "\"Compiled on a $os $version system" \
            "on `date +%Y-%m-%d`.\\n\"" ;; \
       *) ;; \
     esac; \
     files="../libio/Banner ../crypt/Banner ../linuxthreads/Banner ../resolv/Banner ../linuxthreads_db/Banner ../nis/Banner";        \
     if test -n "$files"; then                \
       echo "\"Available extensions:\\n\"";            \
       sed -e '/^#/d' -e 's/^[[:space:]]*/    /'        \
           -e 's/\(^.*$\)/\"\1\\n\"/' $files;        \
     fi) > version-info.hT
mv -f version-info.hT version-info.h
gcc -M version.c -O2 -Wall -Winline -Wstrict-prototypes -Wwrite-strings -g      -I../include -I.  -I.. -I../libio  -I../sysdeps/i386/elf -I../linuxthreads/sysdeps/unix/sysv/linux/i386 -I../linuxthreads/sysdeps/unix/sysv/linux -I../linuxthreads/sysdeps/pthread -I../sysdeps/pthread -I../linuxthreads/sysdeps/unix/sysv -I../linuxthreads/sysdeps/unix -I../linuxthreads/sysdeps/i386/i686 -I../linuxthreads/sysdeps/i386 -I../sysdeps/unix/sysv/linux/i386/i686 -I../sysdeps/unix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/inet -I../sysdeps/unix/sysv/i386 -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../sysdeps/i386/i686 -I../sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../sysdeps/i386 -I../sysdeps/wordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sysdeps/generic/elf -I../sysdeps/generic   -D_LIBC_REENTRANT -include ../include/libc-symbols.h     -DHAVE_INITFINI  | sed -e 's,version\.o,version.o version.os version.op version.og version.ob version.oS version.d,'  > version.T
mv -f version.T version.d 
make[1]: Leaving directory `/home/david/Applications/glibc-2.2.5/csu'
make[1]: Entering directory `/home/david/Applications/glibc-2.2.5/csu'
gcc ../sysdeps/unix/sysv/linux/init-first.c -c -O2 -Wall -Winline -Wstrict-prototypes -Wwrite-strings -g      -I../include -I.  -I.. -I../libio  -I../sysdeps/i386/elf -I../linuxthreads/sysdeps/unix/sysv/linux/i386 -I../linuxthreads/sysdeps/unix/sysv/linux -I../linuxthreads/sysdeps/pthread -I../sysdeps/pthread -I../linuxthreads/sysdeps/unix/sysv -I../linuxthreads/sysdeps/unix -I../linuxthreads/sysdeps/i386/i686 -I../linuxthreads/sysdeps/i386 -I../sysdeps/unix/sysv/linux/i386/i686 -I../sysdeps/unix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/inet -I../sysdeps/unix/sysv/i386 -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../sysdeps/i386/i686 -I../sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../sysdeps/i386 -I../sysdeps/wordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sysdeps/generic/elf -I../sysdeps/generic   -D_LIBC_REENTRANT -include ../include/libc-symbols.h     -DHAVE_INITFINI -o init-first.o
In file included from ../include/stdlib.h:7,
                 from ../sysdeps/unix/sysv/linux/init-first.c:21:
../stdlib/stdlib.h:557: warning: ‘__malloc__’ attribute ignored
In file included from ../sysdeps/unix/sysv/linux/init-first.c:21:
../include/stdlib.h:64: warning: ‘__malloc__’ attribute ignored
In file included from ../include/pthread.h:1,
                 from ../linuxthreads/sysdeps/pthread/bits/libc-lock.h:23,
                 from ../sysdeps/generic/ldsodefs.h:34,
                 from ../sysdeps/unix/sysv/linux/ldsodefs.h:25,
                 from ../sysdeps/unix/sysv/linux/init-first.c:32:
../linuxthreads/sysdeps/pthread/pthread.h:163: error: expected ‘;’, ‘,’ or ‘)’ before ‘__thread’
../linuxthreads/sysdeps/pthread/pthread.h:591: error: storage class specified for parameter ‘type name’
In file included from ../linuxthreads/sysdeps/pthread/pthread.h:655,
                 from ../include/pthread.h:1,
                 from ../linuxthreads/sysdeps/pthread/bits/libc-lock.h:23,
                 from ../sysdeps/generic/ldsodefs.h:34,
                 from ../sysdeps/unix/sysv/linux/ldsodefs.h:25,
                 from ../sysdeps/unix/sysv/linux/init-first.c:32:
../linuxthreads/sysdeps/unix/sysv/linux/bits/sigthread.h:36: error: storage class specified for parameter ‘type name’
make[1]: *** [init-first.o] Error 1
make[1]: Leaving directory `/home/david/Applications/glibc-2.2.5/csu'
make: *** [csu/subdir_lib] Error 2
```I'm pretty new to Linux and have never successfully compiled anything before, so I have no idea where to go from here. Can somebody help me out? (Alternatively, if somebody could point me to a place where I could get glibc already compiled (2.2.5 or 2.4.1 would work), that would be great too. I just need to get MATLAB working.

Thanks!

David

---

### Post by SevenMachines on 2010-01-10
building quite old versions of glibc on newer systems can be a royal pain as i remember (at least for me :) ) if you can get something useful ( only locally specific, used to get matlab working as you mention ) out of the older versions at [http://archive.debian.org/debian/pool/main/g/glibc/](http://archive.debian.org/debian/pool/main/g/glibc/)
i'd try that instead

---

### Post by drs86 on 2010-01-11
Thanks. I managed to get an old library, but unfortunately I still can't get MATLAB to work because apparently it is only one particular part of the program (the symbolic math toolbox) that needs the old library and the rest wants to use the default system libs. I would apparently have to have a dynamic linker to go between the two. Way too complicated for me. Oh well. I can still use the majority of the program, just not the symbolic math toolbox.

---

