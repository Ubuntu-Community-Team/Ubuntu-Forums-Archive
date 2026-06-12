---
title: "Problem with building gcc-2.95.3 on ubuntu 10.04"
date: 2011-06-02
forum: Programming Talk
---

### Post by wxyywxyy on 2011-06-02
I got the message as below when I install the gcc-2.95.3 on ubuntu 10.04, is there any one have ever seen this problem? Thanks.
 
Aborted
 
rm -f libgcc1.S
 
mv tmplibgcc1.a libgcc1-asm.a
 
make[3]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
 
rm -rf tmplibgcc.a tmpcopy
 
mkdir tmpcopy
 
if [ xlibgcc1-asm.a != x ]; \
 
then (cd tmpcopy; arm-linux-ar x ../libgcc1-asm.a); \
 
else true; \
 
fi
 
(cd tmpcopy; chmod +w * > /dev/null 2>&1)
 
make[2]: [stmp-multilib-sub] Error 1 (ignored)
 
(cd tmpcopy; arm-linux-ar x ../libgcc2.a)
 
(cd tmpcopy; arm-linux-ar rc ../tmplibgcc.a *.o)
 
arm-linux-ar: *.o: No such file or directory
 
make[2]: *** [stmp-multilib-sub] Error 1
 
make[2]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc' 
make[1]: *** [stmp-multilib] Error 1
 
make[1]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
 
make: *** [all-gcc] Error 2
 
 
 
 
Xinying

---

### Post by unknownPoster on 2011-06-02
gcc 2.95 is over 10 years old. Are you sure that's the version you need rather than gcc 4?

---

### Post by wxyywxyy on 2011-06-02
Yes, I need that for SimpleScalar ARM Cross Compiler.

---

### Post by unknownPoster on 2011-06-02
Well it looks like make is failing on "arm-linux-ar: *.o: No such file or directory"

Are you compiling on an ARM processor?

---

### Post by wxyywxyy on 2011-06-02
No, running on intel processor. It's used for cross platform compiling.
 
I think there might be some problem happen earlier. So I post more error message below.
 
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfd96000-bfdac000 rw-p 00000000 00:00 0 [stack]
Aborted
for name in _eh; \
do \
echo ${name}; \
/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include -O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -fexceptions -I. -I. -I./config -I./../include -c \
-DL${name} ./libgcc2.c -o ${name}.o; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
arm-linux-ar rc tmplibgcc2.a ${name}.o; \
rm -f ${name}.o; \
done
_eh
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08530000-08551000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfb44000-bfb5a000 rw-p 00000000 00:00 0 [stack]
Aborted
if [ x != x ]; then \
for name in _pack_sf _unpack_sf _addsub_sf _mul_sf _div_sf _fpcmp_parts_sf _compare_sf _eq_sf _ne_sf _gt_sf _ge_sf _lt_sf _le_sf _si_to_sf _sf_to_si _negate_sf _make_sf _sf_to_df; \
do \
echo ${name}; \
/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include -O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -I. -I. -I./config -I./../include -c -DL${name} \
-DFINE_GRAINED_LIBRARIES -o ${name}.o; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
arm-linux-ar rc tmplibgcc2.a ${name}.o; \
rm -f ${name}.o; \
done; \
else true; fi;
if [ x != x ]; then \
for name in _pack_df _unpack_df _addsub_df _mul_df _div_df _fpcmp_parts_df _compare_df _eq_df _ne_df _gt_df _ge_df _lt_df _le_df _si_to_df _df_to_si _negate_df _make_df _df_to_sf; \
do \
echo ${name}; \
/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include -O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -I. -I. -I./config -I./../include -c -DL${name} \
-DFINE_GRAINED_LIBRARIES -o ${name}.o; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
arm-linux-ar rc tmplibgcc2.a ${name}.o; \
rm -f ${name}.o; \
done; \
else true; fi;
for file in ./frame.c cplib2.txt ; do \
name=`echo ${file} | sed -e 's/[.][cSo]$//' -e 's/[.]asm$//' -e 's/[.]txt$//'`; \
oname=` echo ${name} | sed -e 's,.*/,,'`; \
if [ ${name}.txt = ${file} ]; then \
for f in .. `cat ${file}`; do if [ x${f} != x.. ]; then \
make GCC_FOR_TARGET="/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include" \
AR_FOR_TARGET="arm-linux-ar" \
AR_FLAGS_FOR_TARGET="rc" CC="gcc-3.4" \
CFLAGS="-g" HOST_PREFIX="" \
HOST_PREFIX_1="loser-" \
LANGUAGES="c" \
LIBGCC2_CFLAGS="-O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED " ${f}; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
arm-linux-ar rc tmplibgcc2.a ${f}; \
rm -f ${f}; \
else true; \
fi; done; \
else \
echo ${name}; \
if [ ${name}.asm = ${file} ]; then \
cp ${file} ${name}.s || exit 1; file=${name}.s; \
else true; fi; \
/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include -O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -I. -I. -I./config -I./../include -c ${file}; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
arm-linux-ar rc tmplibgcc2.a ${oname}.o; \
rm -f ${name}.s ${oname}.o; \
fi; \
done
./frame
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08b06000-08b27000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bffab000-bffc1000 rw-p 00000000 00:00 0 [stack]
Aborted
mv tmplibgcc2.a libgcc2.a
make[3]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
if [ xlibgcc1-asm.a != xlibgcc1-asm.a ]; \
then true; \
else rm -f libgcc1-asm.a; \
fi
if [ xlibgcc1-asm.a != xlibgcc1-asm.a ]; \
then true; \
else \
make GCC_FOR_TARGET="/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include" \
AR_FOR_TARGET="arm-linux-ar" \
AR_FLAGS_FOR_TARGET="rc" \
CC="gcc-3.4" CFLAGS="-g" \
HOST_PREFIX="" HOST_PREFIX_1="loser-" \
LANGUAGES="c" \
LIBGCC2_CFLAGS="-O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED " libgcc1-asm.a; \
fi
make[3]: Entering directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
if [ -f libgcc2.ready ] ; then \
true; \
else \
touch libgcc2.ready; \
fi
rm -f tmplibgcc1.a libgcc1.S
cp ./config/arm/lib1funcs.asm libgcc1.S
for name in _udivsi3 _divsi3 _umodsi3 _modsi3 _dvmd_lnx; \
do \
echo ${name}; \
/home/xinying/cross-arm/gcc-2.95.2/gcc/xgcc -B/home/xinying/cross-arm/gcc-2.95.2/gcc/ -B/home/xinying/cross-arm/arm-linux/bin/ -I/home/xinying/cross-arm/arm-linux/include -O2 -DCROSS_COMPILE -DIN_GCC -g -I./include -fomit-frame-pointer -fPIC -Dinhibit_libc -D__gthr_posix_h -g0 -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -I. -I. -I./config -I./../include -c -DL${name} libgcc1.S; \
if [ $? -eq 0 ] ; then true; else exit 1; fi; \
mv libgcc1.o ${name}.o; \
arm-linux-ar rc tmplibgcc1.a ${name}.o; \
rm -f ${name}.o; \
done
_udivsi3
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08fdd000-08ffe000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfe86000-bfe9c000 rw-p 00000000 00:00 0 [stack]
Aborted
_divsi3
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
091a7000-091c8000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfa03000-bfa19000 rw-p 00000000 00:00 0 [stack]
Aborted
_umodsi3
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
09f94000-09fb5000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfd29000-bfd3f000 rw-p 00000000 00:00 0 [stack]
Aborted
_modsi3
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08870000-08891000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bffe2000-bfff8000 rw-p 00000000 00:00 0 [stack]
Aborted
_dvmd_lnx
*** buffer overflow detected ***: arm-linux-ar terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0x40110390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0x4010f2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0x4010ea08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x40097afe]
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xd8)[0x4008b5f8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x2aee)[0x4006d6fe]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0x4010eabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4010e9fd]
arm-linux-ar[0x804fd45]
arm-linux-ar[0x804e0db]
arm-linux-ar[0x805072e]
arm-linux-ar[0x8052dc2]
arm-linux-ar[0x804b74c]
arm-linux-ar[0x804c237]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x40044bd6]
arm-linux-ar[0x80496f1]
======= Memory map: ========
08048000-08081000 r-xp 00000000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08081000-08082000 r--p 00038000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
08082000-08083000 rw-p 00039000 08:01 310573 /home/xinying/cross-arm/bin/arm-linux-ar
0932f000-09350000 rw-p 00000000 00:00 0 [heap]
40000000-4001b000 r-xp 00000000 08:01 133147 /lib/ld-2.11.1.so
4001b000-4001c000 r--p 0001a000 08:01 133147 /lib/ld-2.11.1.so
4001c000-4001d000 rw-p 0001b000 08:01 133147 /lib/ld-2.11.1.so
4001d000-4001e000 r-xp 00000000 00:00 0 [vdso]
4001e000-40020000 rw-p 00000000 00:00 0 
40020000-40021000 r--p 00000000 08:01 302869 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40021000-40028000 r--s 00000000 08:01 269630 /usr/lib/gconv/gconv-modules.cache
40028000-4002b000 rw-p 00000000 00:00 0 
4002e000-40181000 r-xp 00000000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40181000-40182000 ---p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40182000-40184000 r--p 00153000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40184000-40185000 rw-p 00155000 08:01 262835 /lib/tls/i686/cmov/libc-2.11.1.so
40185000-40189000 rw-p 00000000 00:00 0 
40197000-401b4000 r-xp 00000000 08:01 133205 /lib/libgcc_s.so.1
401b4000-401b5000 r--p 0001c000 08:01 133205 /lib/libgcc_s.so.1
401b5000-401b6000 rw-p 0001d000 08:01 133205 /lib/libgcc_s.so.1
bfa86000-bfa9c000 rw-p 00000000 00:00 0 [stack]
Aborted
rm -f libgcc1.S
mv tmplibgcc1.a libgcc1-asm.a
make[3]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
rm -rf tmplibgcc.a tmpcopy
mkdir tmpcopy
if [ xlibgcc1-asm.a != x ]; \
then (cd tmpcopy; arm-linux-ar x ../libgcc1-asm.a); \
else true; \
fi
(cd tmpcopy; chmod +w * > /dev/null 2>&1)
make[2]: [stmp-multilib-sub] Error 1 (ignored)
(cd tmpcopy; arm-linux-ar x ../libgcc2.a)
(cd tmpcopy; arm-linux-ar rc ../tmplibgcc.a *.o)
arm-linux-ar: *.o: No such file or directory
make[2]: *** [stmp-multilib-sub] Error 1
make[2]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
make[1]: *** [stmp-multilib] Error 1
make[1]: Leaving directory `/home/xinying/cross-arm/gcc-2.95.2/gcc'
make: *** [all-gcc] Error 2
 
Xinying

---

