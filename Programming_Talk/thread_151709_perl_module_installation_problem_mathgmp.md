---
title: "perl module installation problem math::gmp"
date: 2006-03-28
forum: Programming Talk
---

### Post by danran on 2006-03-28
Hi, i'm using: Linux sevilla 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux - Breezy Badger 5.10

I'm trying to install Net::SSH::Perl but it keeps failing out when it gets to Math::GMP, which is a prerequisite.  So I tried doing it manually with the command below:

**dwozniak@sevilla:~$ sudo perl -MCPAN -e 'install Math::GMP'**
CPAN: Storable loaded ok
Going to read /home/dwozniak/.cpan/Metadata
  Database was generated on Tue, 28 Mar 2006 10:45:02 GMT
Running install for module Math::GMP
Running make for C/CH/CHIPT/Math-GMP-2.04.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/dwozniak/.cpan/sources/authors/id/C/CH/CHIPT/Math-GMP-2.04.tar.gz ok
Scanning cache /home/dwozniak/.cpan/build for sizes
Deleting from cache: /home/dwozniak/.cpan/build/URI-1.35 (24.5>10.0 MB)
Deleting from cache: /home/dwozniak/.cpan/build/HTML-Tagset-3.10 (23.9>10.0 MB)
Deleting from cache: /home/dwozniak/.cpan/build/HTML-Parser-3.51 (23.8>10.0 MB)
Deleting from cache: /home/dwozniak/.cpan/build/libwww-perl-5.805 (23.2>10.0 MB)
Deleting from cache: /home/dwozniak/.cpan/build/Math-Pari-2.010704 (21.2>10.0 MB)
Math-GMP-2.04/
Math-GMP-2.04/Changes
Math-GMP-2.04/COPYING.LIB
Math-GMP-2.04/MANIFEST
Math-GMP-2.04/typemap
Math-GMP-2.04/GMP.xs
Math-GMP-2.04/t/
Math-GMP-2.04/t/gmppm.t
Math-GMP-2.04/lib/
Math-GMP-2.04/lib/Math/
Math-GMP-2.04/lib/Math/GMP.pm
Math-GMP-2.04/INSTALL
Math-GMP-2.04/Makefile.PL
Math-GMP-2.04/README
Math-GMP-2.04/LICENSE
Removing previously used /home/dwozniak/.cpan/build/Math-GMP-2.04

  CPAN.pm: Going to build C/CH/CHIPT/Math-GMP-2.04.tar.gz

Checking if your kit is complete...
Looks good
Note (probably harmless): No library found for -lgmp
Writing Makefile for Math::GMP
cp lib/Math/GMP.pm blib/lib/Math/GMP.pm
AutoSplitting blib/lib/Math/GMP.pm (blib/lib/auto/Math/GMP)
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  GMP.xs > GMP.xsc && mv GMP.xsc GMP.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.04\" -DXS_VERSION=\"2.04\" -fPIC "-I/usr/lib/perl/5.8/CORE"   GMP.c
GMP.xs:4:17: error: gmp.h: No such file or directory
GMP.c: In function ‘XS_Math__GMP_new_from_scalar’:
GMP.c:91: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:91: error: (Each undeclared identifier is reported only once
GMP.c:91: error: for each function it appears in.)
GMP.c:91: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c: In function ‘XS_Math__GMP_new_from_scalar_with_base’:
GMP.c:111: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:111: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c: In function ‘XS_Math__GMP_destroy’:
GMP.c:129: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:129: error: ‘n’ undeclared (first use in this function)
GMP.c:133: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_stringify_gmp’:
GMP.c:152: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:152: error: ‘n’ undeclared (first use in this function)
GMP.c:161: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_get_str_gmp’:
GMP.c:188: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:188: error: ‘n’ undeclared (first use in this function)
GMP.c:198: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_sizeinbase_gmp’:
GMP.c:225: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:225: error: ‘n’ undeclared (first use in this function)
GMP.c:232: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_uintify_gmp’:
GMP.c:251: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:251: error: ‘n’ undeclared (first use in this function)
GMP.c:257: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_add_ui_gmp’:
GMP.c:276: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:276: error: ‘n’ undeclared (first use in this function)
GMP.c:281: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_intify_gmp’:
GMP.c:299: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:299: error: ‘n’ undeclared (first use in this function)
GMP.c:305: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_mul_2exp_gmp’:
GMP.c:324: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:324: error: ‘n’ undeclared (first use in this function)
GMP.c:326: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:330: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_div_2exp_gmp’:
GMP.c:352: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:352: error: ‘n’ undeclared (first use in this function)
GMP.c:354: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:358: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_powm_gmp’:
GMP.c:380: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:380: error: ‘n’ undeclared (first use in this function)
GMP.c:382: error: ‘mod’ undeclared (first use in this function)
GMP.c:383: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:387: error: syntax error before ‘)’ token
GMP.c:394: error: syntax error before ‘)’ token
GMP.c:401: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_mmod_gmp’:
GMP.c:423: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:423: error: ‘a’ undeclared (first use in this function)
GMP.c:424: error: ‘b’ undeclared (first use in this function)
GMP.c:425: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:429: error: syntax error before ‘)’ token
GMP.c:436: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_mod_2exp_gmp’:
GMP.c:458: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:458: error: ‘in’ undeclared (first use in this function)
GMP.c:460: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:464: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_add_two’:
GMP.c:486: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:486: error: ‘m’ undeclared (first use in this function)
GMP.c:487: error: ‘n’ undeclared (first use in this function)
GMP.c:488: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:492: error: syntax error before ‘)’ token
GMP.c:499: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_sub_two’:
GMP.c:521: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:521: error: ‘m’ undeclared (first use in this function)
GMP.c:522: error: ‘n’ undeclared (first use in this function)
GMP.c:523: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:527: error: syntax error before ‘)’ token
GMP.c:534: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_mul_two’:
GMP.c:556: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:556: error: ‘m’ undeclared (first use in this function)
GMP.c:557: error: ‘n’ undeclared (first use in this function)
GMP.c:558: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:562: error: syntax error before ‘)’ token
GMP.c:569: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_div_two’:
GMP.c:591: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:591: error: ‘m’ undeclared (first use in this function)
GMP.c:592: error: ‘n’ undeclared (first use in this function)
GMP.c:593: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:597: error: syntax error before ‘)’ token
GMP.c:604: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_bdiv_two’:
GMP.c:627: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:627: error: ‘m’ undeclared (first use in this function)
GMP.c:628: error: ‘n’ undeclared (first use in this function)
GMP.xs:293: error: ‘quo’ undeclared (first use in this function)
GMP.xs:294: error: ‘rem’ undeclared (first use in this function)
GMP.c:636: error: syntax error before ‘)’ token
GMP.c:643: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_mod_two’:
GMP.c:669: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:669: error: ‘m’ undeclared (first use in this function)
GMP.c:670: error: ‘n’ undeclared (first use in this function)
GMP.c:671: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:675: error: syntax error before ‘)’ token
GMP.c:682: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_cmp_two’:
GMP.c:704: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:704: error: ‘m’ undeclared (first use in this function)
GMP.c:705: error: ‘n’ undeclared (first use in this function)
GMP.c:711: error: syntax error before ‘)’ token
GMP.c:718: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_legendre’:
GMP.c:737: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:737: error: ‘m’ undeclared (first use in this function)
GMP.c:738: error: ‘n’ undeclared (first use in this function)
GMP.c:744: error: syntax error before ‘)’ token
GMP.c:751: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_jacobi’:
GMP.c:770: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:770: error: ‘m’ undeclared (first use in this function)
GMP.c:771: error: ‘n’ undeclared (first use in this function)
GMP.c:777: error: syntax error before ‘)’ token
GMP.c:784: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_pow_two’:
GMP.c:803: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:803: error: ‘m’ undeclared (first use in this function)
GMP.c:805: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:809: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gcd_two’:
GMP.c:832: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:832: error: ‘m’ undeclared (first use in this function)
GMP.c:833: error: ‘n’ undeclared (first use in this function)
GMP.c:834: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:838: error: syntax error before ‘)’ token
GMP.c:845: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_fib’:
GMP.c:868: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:868: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c: In function ‘XS_Math__GMP_and_two’:
GMP.c:887: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:887: error: ‘m’ undeclared (first use in this function)
GMP.c:888: error: ‘n’ undeclared (first use in this function)
GMP.c:889: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:893: error: syntax error before ‘)’ token
GMP.c:900: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_xor_two’:
GMP.c:922: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:922: error: ‘m’ undeclared (first use in this function)
GMP.c:923: error: ‘n’ undeclared (first use in this function)
GMP.c:924: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:928: error: syntax error before ‘)’ token
GMP.c:935: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_or_two’:
GMP.c:957: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:957: error: ‘m’ undeclared (first use in this function)
GMP.c:958: error: ‘n’ undeclared (first use in this function)
GMP.c:959: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:963: error: syntax error before ‘)’ token
GMP.c:970: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_fac’:
GMP.c:993: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:993: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c: In function ‘XS_Math__GMP_gmp_copy’:
GMP.c:1012: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:1012: error: ‘m’ undeclared (first use in this function)
GMP.c:1013: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:1017: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_tstbit’:
GMP.c:1038: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:1038: error: ‘m’ undeclared (first use in this function)
GMP.c:1045: error: syntax error before ‘)’ token
GMP.c: In function ‘XS_Math__GMP_gmp_sqrt’:
GMP.c:1064: error: ‘mpz_t’ undeclared (first use in this function)
GMP.c:1064: error: ‘m’ undeclared (first use in this function)
GMP.c:1065: error: ‘RETVAL’ undeclared (first use in this function)
GMP.c:1069: error: syntax error before ‘)’ token
make: *** [GMP.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


I'm stumped, any ideas?  Thanks.

--Dan W.](*,)

---

### Post by johnnymac on 2006-03-28
Try installing or updating to a new bundle and then give it a shot.  If that doesn't work, go and download the tar file from CPAN and install it manually...I ran into this same problem when I was installing Net::SSH::Perl and I believe I ended up having to update my CPAN bundle....don't remember exactly

---

### Post by danran on 2006-03-29
I installed the new CPAN bundle but I still had the same results.  So then I downloaded GMP and unzipped it to the .cpan directory.  I ran ./configure and I got:

**dwozniak@sevilla:~/.cpan/gmp-4.2$ sudo ./configure**
checking build system type... pentium4-pc-linux-gnu
checking host system type... pentium4-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking ABI=32
checking compiler gcc -m32 -O2 -fomit-frame-pointer ... yes
checking compiler gcc -m32 -O2 -fomit-frame-pointer has sizeof(long)==4... yes
checking compiler gcc -m32 -O2 -fomit-frame-pointer  -mtune=pentium4... yes
checking whether gcc is good for sse2... yes
checking whether the operating system supports XMM registers... yes
checking compiler gcc -m32 -O2 -fomit-frame-pointer -mtune=pentium4  -march=pentium4... yes
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
checking build system compiler gcc... yes
checking for build system preprocessor... gcc -E
checking for build system executable suffix...
checking whether build system compiler is ANSI... yes
checking for build system compiler math library... -lm
checking for egrep... grep -E
checking if the assembler knows about MMX instructions... yes
checking if the assembler knows about SSE2 instructions... yes
using ABI="32"
      CC="gcc"
      CFLAGS="-m32 -O2 -fomit-frame-pointer -mtune=pentium4 -march=pentium4"
      CPPFLAGS=""
      MPN_PATH=" x86/pentium4/sse2 x86/pentium4/mmx x86/pentium4 x86 generic"
checking for function prototypes... yes
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
checking for string.h... (cached) yes
checking for ar... ar
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... (cached) ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking invent.h usability... no
checking invent.h presence... no
checking for invent.h... no
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking sys/attributes.h usability... no
checking sys/attributes.h presence... no
checking for sys/attributes.h... no
checking sys/iograph.h usability... no
checking sys/iograph.h presence... no
checking for sys/iograph.h... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/processor.h usability... no
checking sys/processor.h presence... no
checking for sys/processor.h... no
checking sys/pstat.h usability... no
checking sys/pstat.h presence... no
checking for sys/pstat.h... no
checking sys/sysinfo.h usability... yes
checking sys/sysinfo.h presence... yes
checking for sys/sysinfo.h... yes
checking sys/syssgi.h usability... no
checking sys/syssgi.h presence... no
checking for sys/syssgi.h... no
checking sys/systemcfg.h usability... no
checking sys/systemcfg.h presence... no
checking for sys/systemcfg.h... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for sys/resource.h... yes
checking for sys/sysctl.h... yes
checking for machine/hal_sysinfo.h... no
checking whether fgetc is declared... yes
checking whether fscanf is declared... yes
checking whether optarg is declared... yes
checking whether ungetc is declared... yes
checking whether vfprintf is declared... yes
checking whether sys_errlist is declared... yes
checking whether sys_nerr is declared... yes
checking return type of signal handlers... void
checking for intmax_t... yes
checking for long double... yes
checking for long long... yes
checking for ptrdiff_t... yes
checking for quad_t... yes
checking for uint_least32_t... yes
checking for preprocessor stringizing operator... yes
checking for working volatile... yes
checking for C/C++ restrict keyword... __restrict
checking whether <stdarg.h> exists and works... yes
checking whether gcc __attribute__ ((const)) works... yes
checking whether gcc __attribute__ ((malloc)) works... yes
checking whether gcc __attribute__ ((mode (XX))) works... yes
checking whether gcc __attribute__ ((noreturn)) works... yes
checking for inline... inline
checking for cos in -lm... yes
checking for working alloca.h... yes
checking for alloca (via gmp-impl.h)... yes
checking how to allocate temporary memory... alloca
checking whether byte ordering is bigendian... no
checking format of `double' floating point... IEEE little endian
checking for alarm... yes
checking for attr_get... no
checking for clock... yes
checking for clock_gettime... no
checking for cputime... no
checking for getpagesize... yes
checking for getrusage... yes
checking for gettimeofday... yes
checking for getsysinfo... no
checking for localeconv... yes
checking for memset... yes
checking for mmap... yes
checking for mprotect... yes
checking for nl_langinfo... yes
checking for obstack_vprintf... yes
checking for popen... yes
checking for processor_info... no
checking for pstat_getprocessor... no
checking for raise... yes
checking for read_real_time... no
checking for sigaction... yes
checking for sigaltstack... yes
checking for sigstack... yes
checking for syssgi... no
checking for strchr... yes
checking for strerror... yes
checking for strnlen... yes
checking for strtol... yes
checking for strtoul... yes
checking for sysconf... yes
checking for sysctl... yes
checking for sysctlbyname... no
checking for times... yes
checking for vsnprintf... yes
checking whether vsnprintf works... yes
checking whether sscanf needs writable input... no
checking for struct pst_processor.psp_iticksperclktick... no
checking for suitable m4... configure: error: No usable m4 in $PATH or /usr/5bin (see config.log for reasons).

[COLOR="Red"]Then I ran make and I got this:[/COLOR]
**dwozniak@sevilla:~/.cpan/gmp-4.2$ sudo make**
make: *** No targets specified and no makefile found.  Stop.
[U]
Now, I have build-essentials installed, but I still get the error above.  Any ideas?  Thanks for the tips already.[/U]

--Dan W.](*,)

---

### Post by danran on 2006-03-30
Got it working.  I downloaded m4 from Synaptic and gmp then compiled fine.  Net::SSH::Perl also compiled fine after the gmp dependency was met.

--Dan W.

---

### Post by johnnymac on 2006-03-30
Awesome!!  I just ran into the issue again on another system so I'm going to try your method...seems easier than mine :)

---

