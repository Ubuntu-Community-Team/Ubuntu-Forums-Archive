---
title: "Successfully built GCC Cross Compiler Toolchain. How Do I Setup Environment Variables"
date: 2012-06-03
forum: Packaging and Compiling Programs
---

### Post by monsterhunter445 on 2012-06-03
I have successfully built a GCC cross compiler toolchain specifically for OS development.  How do I setup enviornment variables, properly so that I can use the toolchain without affecting the GCC toolchain that came with Ubuntu. The toolchain is located in the path /home/Home/local. The directory and file listing is below:
```
    local:
    total 40
    drwxrwxr-x  8 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwx------ 27 monsterdev monsterdev 12288 Jun  3 19:34 ..
    drwxrwxr-x  2 monsterdev monsterdev  4096 Jun  3 13:37 bin
    drwxrwxr-x  2 monsterdev monsterdev  4096 Jun  3 13:24 include
    drwxrwxr-x  3 monsterdev monsterdev  4096 Jun  3 13:37 lib
    drwxrwxr-x  3 monsterdev monsterdev  4096 Jun  3 13:37 libexec
    drwxrwxr-x  6 monsterdev monsterdev  4096 Jun  3 13:24 share
    drwxrwxr-x  5 monsterdev monsterdev  4096 Jun  3 13:39 x86_64-pc-os
    
    local/bin:
    total 52604
    drwxrwxr-x 2 monsterdev monsterdev    4096 Jun  3 13:37 .
    drwxrwxr-x 8 monsterdev monsterdev    4096 Jun  3 13:37 ..
    -rwxr-xr-x 1 monsterdev monsterdev 3220952 Jun  3 13:19 x86_64-pc-os-addr2line
    -rwxr-xr-x 2 monsterdev monsterdev 3385257 Jun  3 13:19 x86_64-pc-os-ar
    -rwxr-xr-x 2 monsterdev monsterdev 4872363 Jun  3 13:19 x86_64-pc-os-as
    -rwxr-xr-x 2 monsterdev monsterdev  669352 Jun  3 13:37 x86_64-pc-os-c++
    -rwxr-xr-x 1 monsterdev monsterdev 3197898 Jun  3 13:19 x86_64-pc-os-c++filt
    -rwxr-xr-x 1 monsterdev monsterdev  667428 Jun  3 13:37 x86_64-pc-os-cpp
    -rwxr-xr-x 2 monsterdev monsterdev  669352 Jun  3 13:37 x86_64-pc-os-g++
    -rwxr-xr-x 2 monsterdev monsterdev  664501 Jun  3 13:37 x86_64-pc-os-gcc
    -rwxr-xr-x 2 monsterdev monsterdev  664501 Jun  3 13:37 x86_64-pc-os-gcc-4.5.0
    -rwxr-xr-x 1 monsterdev monsterdev   16073 Jun  3 13:37 x86_64-pc-os-gccbug
    -rwxr-xr-x 1 monsterdev monsterdev  118441 Jun  3 13:37 x86_64-pc-os-gcov
    -rwxr-xr-x 1 monsterdev monsterdev  677072 Jun  3 13:37 x86_64-pc-os-gfortran
    -rwxr-xr-x 1 monsterdev monsterdev 3681740 Jun  3 13:19 x86_64-pc-os-gprof
    -rwxr-xr-x 2 monsterdev monsterdev 4255437 Jun  3 13:19 x86_64-pc-os-ld
    -rwxr-xr-x 2 monsterdev monsterdev 3273292 Jun  3 13:19 x86_64-pc-os-nm
    -rwxr-xr-x 2 monsterdev monsterdev 4032399 Jun  3 13:19 x86_64-pc-os-objcopy
    -rwxr-xr-x 2 monsterdev monsterdev 4840114 Jun  3 13:19 x86_64-pc-os-objdump
    -rwxr-xr-x 2 monsterdev monsterdev 3385248 Jun  3 13:19 x86_64-pc-os-ranlib
    -rwxr-xr-x 1 monsterdev monsterdev  841102 Jun  3 13:19 x86_64-pc-os-readelf
    -rwxr-xr-x 1 monsterdev monsterdev 3247907 Jun  3 13:19 x86_64-pc-os-size
    -rwxr-xr-x 1 monsterdev monsterdev 3223604 Jun  3 13:19 x86_64-pc-os-strings
    -rwxr-xr-x 2 monsterdev monsterdev 4032390 Jun  3 13:19 x86_64-pc-os-strip
    
    local/include:
    total 196
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:24 .
    drwxrwxr-x 8 monsterdev monsterdev  4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev 86236 Jun  3 13:22 gmp.h
    -rw-r--r-- 1 monsterdev monsterdev 13031 Jun  3 13:24 mpc.h
    -rw-r--r-- 1 monsterdev monsterdev  6165 Jun  3 13:24 mpf2mpfr.h
    -rw-r--r-- 1 monsterdev monsterdev 42837 Jun  3 13:24 mpfr.h
    
    local/lib:
    total 3480
    drwxrwxr-x 3 monsterdev monsterdev    4096 Jun  3 13:37 .
    drwxrwxr-x 8 monsterdev monsterdev    4096 Jun  3 13:37 ..
    drwxrwxr-x 3 monsterdev monsterdev    4096 Jun  3 13:37 gcc
    -rw-r--r-- 1 monsterdev monsterdev 1183726 Jun  3 13:22 libgmp.a
    -rwxr-xr-x 1 monsterdev monsterdev     892 Jun  3 13:22 libgmp.la
    -rw-r--r-- 1 monsterdev monsterdev 1274800 Jun  3 13:19 libiberty.a
    -rw-r--r-- 1 monsterdev monsterdev  200702 Jun  3 13:24 libmpc.a
    -rwxr-xr-x 1 monsterdev monsterdev    1052 Jun  3 13:24 libmpc.la
    -rw-r--r-- 1 monsterdev monsterdev  815898 Jun  3 13:24 libmpfr.a
    -rwxr-xr-x 1 monsterdev monsterdev    1003 Jun  3 13:24 libmpfr.la
    
    local/lib/gcc:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 x86_64-pc-os
    
    local/lib/gcc/x86_64-pc-os:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x 7 monsterdev monsterdev 4096 Jun  3 13:37 4.5.0
    
    local/lib/gcc/x86_64-pc-os/4.5.0:
    total 28
    drwxrwxr-x 7 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxr-xr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 finclude
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 include
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 include-fixed
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 install-tools
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 plugin
    
    local/lib/gcc/x86_64-pc-os/4.5.0/finclude:
    total 8
    drwxr-xr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 7 monsterdev monsterdev 4096 Jun  3 13:37 ..
    
    local/lib/gcc/x86_64-pc-os/4.5.0/include:
    total 672
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwxrwxr-x 7 monsterdev monsterdev  4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev  1799 Jun  3 13:37 abmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  3089 Jun  3 13:37 ammintrin.h
    -rw-r--r-- 1 monsterdev monsterdev 47999 Jun  3 13:37 avxintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  1161 Jun  3 13:37 bmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  5414 Jun  3 13:37 cpuid.h
    -rw-r--r-- 1 monsterdev monsterdev  2598 Jun  3 13:37 cross-stdarg.h
    -rw-r--r-- 1 monsterdev monsterdev 49931 Jun  3 13:37 emmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  7847 Jun  3 13:37 float.h
    -rw-r--r-- 1 monsterdev monsterdev  8978 Jun  3 13:37 fma4intrin.h
    -rw-r--r-- 1 monsterdev monsterdev  6173 Jun  3 13:37 ia32intrin.h
    -rw-r--r-- 1 monsterdev monsterdev  1537 Jun  3 13:37 immintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  1279 Jun  3 13:37 iso646.h
    -rw-r--r-- 1 monsterdev monsterdev  3219 Jun  3 13:37 lwpintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  6632 Jun  3 13:37 mm3dnow.h
    -rw-r--r-- 1 monsterdev monsterdev 30625 Jun  3 13:37 mmintrin.h
    -rw-rw-r-- 1 monsterdev monsterdev  2221 Jun  3 13:37 mm_malloc.h
    -rw-r--r-- 1 monsterdev monsterdev  1379 Jun  3 13:37 nmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  4272 Jun  3 13:37 pmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  1599 Jun  3 13:37 popcntintrin.h
    -rw-r--r-- 1 monsterdev monsterdev 27677 Jun  3 13:37 smmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  4203 Jun  3 13:37 stdarg.h
    -rw-r--r-- 1 monsterdev monsterdev  1451 Jun  3 13:37 stdbool.h
    -rw-r--r-- 1 monsterdev monsterdev 12542 Jun  3 13:37 stddef.h
    -rw-r--r-- 1 monsterdev monsterdev  6001 Jun  3 13:37 stdfix.h
    -rw-r--r-- 1 monsterdev monsterdev  8063 Jun  3 13:37 tgmath.h
    -rw-r--r-- 1 monsterdev monsterdev  8222 Jun  3 13:37 tmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev 10246 Jun  3 13:37 unwind.h
    -rw-r--r-- 1 monsterdev monsterdev   139 Jun  3 13:37 varargs.h
    -rw-r--r-- 1 monsterdev monsterdev  4359 Jun  3 13:37 wmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev  1909 Jun  3 13:37 x86intrin.h
    -rw-r--r-- 1 monsterdev monsterdev 41731 Jun  3 13:37 xmmintrin.h
    -rw-r--r-- 1 monsterdev monsterdev 28366 Jun  3 13:37 xopintrin.h
    
    local/lib/gcc/x86_64-pc-os/4.5.0/include-fixed:
    total 44
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 7 monsterdev monsterdev 4096 Jun  3 13:37 ..
    -rw-rw-r-- 1 monsterdev monsterdev 3753 Jun  3 13:37 limits.h
    -rw-r--r-- 1 monsterdev monsterdev  750 Jun  3 13:37 README
    -rw-r--r-- 1 monsterdev monsterdev  330 Jun  3 13:37 syslimits.h
    
    local/lib/gcc/x86_64-pc-os/4.5.0/install-tools:
    total 60
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 7 monsterdev monsterdev 4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev    2 Jun  3 13:37 fixinc_list
    -rw-r--r-- 1 monsterdev monsterdev  330 Jun  3 13:37 gsyslimits.h
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 include
    -rw-r--r-- 1 monsterdev monsterdev    8 Jun  3 13:37 macro_list
    -rw-rw-r-- 1 monsterdev monsterdev  134 Jun  3 13:37 mkheaders.conf
    
    local/lib/gcc/x86_64-pc-os/4.5.0/install-tools/include:
    total 32
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev 3753 Jun  3 13:37 limits.h
    -rw-r--r-- 1 monsterdev monsterdev  750 Jun  3 13:37 README
    
    local/lib/gcc/x86_64-pc-os/4.5.0/plugin:
    total 28
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwxrwxr-x 7 monsterdev monsterdev  4096 Jun  3 13:37 ..
    drwxrwxr-x 4 monsterdev monsterdev 20480 Jun  3 13:37 include
    
    local/lib/gcc/x86_64-pc-os/4.5.0/plugin/include:
    total 3192
    drwxrwxr-x 4 monsterdev monsterdev  20480 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev   2304 Jun  3 13:37 alias.h
    -rw-r--r-- 1 monsterdev monsterdev     93 Jun  3 13:37 all-tree.def
    -rw-r--r-- 1 monsterdev monsterdev  13917 Jun  3 13:37 ansidecl.h
    -rw-r--r-- 1 monsterdev monsterdev  40922 Jun  3 13:37 auto-host.h
    -rw-r--r-- 1 monsterdev monsterdev  34564 Jun  3 13:37 basic-block.h
    -rw-r--r-- 1 monsterdev monsterdev   9120 Jun  3 13:37 b-header-vars
    -rw-r--r-- 1 monsterdev monsterdev  19124 Jun  3 13:37 bitmap.h
    -rw-r--r-- 1 monsterdev monsterdev  66653 Jun  3 13:37 builtins.def
    -rw-r--r-- 1 monsterdev monsterdev    170 Jun  3 13:37 bversion.h
    -rw-r--r-- 1 monsterdev monsterdev   2362 Jun  3 13:37 c-common.def
    -rw-r--r-- 1 monsterdev monsterdev  42609 Jun  3 13:37 c-common.h
    -rw-r--r-- 1 monsterdev monsterdev   7924 Jun  3 13:37 cfghooks.h
    -rw-r--r-- 1 monsterdev monsterdev  18700 Jun  3 13:37 cfgloop.h
    -rw-r--r-- 1 monsterdev monsterdev  26108 Jun  3 13:37 cgraph.h
    -rw-r--r-- 1 monsterdev monsterdev   3263 Jun  3 13:37 cif-code.def
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:37 config
    -rw-r--r-- 1 monsterdev monsterdev    570 Jun  3 13:37 configargs.h
    -rw-r--r-- 1 monsterdev monsterdev    217 Jun  3 13:37 config.h
    -rw-r--r-- 1 monsterdev monsterdev   4256 Jun  3 13:37 coretypes.h
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:37 cp
    -rw-r--r-- 1 monsterdev monsterdev   2774 Jun  3 13:37 cppdefault.h
    -rw-r--r-- 1 monsterdev monsterdev  34699 Jun  3 13:37 cpplib.h
    -rw-r--r-- 1 monsterdev monsterdev   4184 Jun  3 13:37 c-pragma.h
    -rw-r--r-- 1 monsterdev monsterdev   8963 Jun  3 13:37 c-pretty-print.h
    -rw-r--r-- 1 monsterdev monsterdev   8904 Jun  3 13:37 debug.h
    -rw-r--r-- 1 monsterdev monsterdev  34329 Jun  3 13:37 defaults.h
    -rw-r--r-- 1 monsterdev monsterdev   2036 Jun  3 13:37 diagnostic.def
    -rw-r--r-- 1 monsterdev monsterdev   9801 Jun  3 13:37 diagnostic.h
    -rw-r--r-- 1 monsterdev monsterdev   6659 Jun  3 13:37 double-int.h
    -rw-r--r-- 1 monsterdev monsterdev   1901 Jun  3 13:37 emit-rtl.h
    -rw-r--r-- 1 monsterdev monsterdev  14092 Jun  3 13:37 except.h
    -rw-r--r-- 1 monsterdev monsterdev   2118 Jun  3 13:37 filenames.h
    -rw-r--r-- 1 monsterdev monsterdev   3678 Jun  3 13:37 fixed-value.h
    -rw-r--r-- 1 monsterdev monsterdev  13251 Jun  3 13:37 flags.h
    -rw-r--r-- 1 monsterdev monsterdev  25872 Jun  3 13:37 function.h
    -rw-r--r-- 1 monsterdev monsterdev   4449 Jun  3 13:37 gcc-plugin.h
    -rw-r--r-- 1 monsterdev monsterdev  26651 Jun  3 13:37 genrtl.h
    -rw-r--r-- 1 monsterdev monsterdev  12750 Jun  3 13:37 ggc.h
    -rw-r--r-- 1 monsterdev monsterdev  13737 Jun  3 13:37 gimple.def
    -rw-r--r-- 1 monsterdev monsterdev 116601 Jun  3 13:37 gimple.h
    -rw-r--r-- 1 monsterdev monsterdev   2431 Jun  3 13:37 gsstruct.def
    -rw-r--r-- 1 monsterdev monsterdev  77612 Jun  3 13:37 gtype-desc.h
    -rw-r--r-- 1 monsterdev monsterdev  21027 Jun  3 13:37 hard-reg-set.h
    -rw-r--r-- 1 monsterdev monsterdev   7279 Jun  3 13:37 hashtab.h
    -rw-r--r-- 1 monsterdev monsterdev   1116 Jun  3 13:37 highlev-plugin-common.h
    -rw-r--r-- 1 monsterdev monsterdev   6276 Jun  3 13:37 hwint.h
    -rw-r--r-- 1 monsterdev monsterdev   1398 Jun  3 13:37 incpath.h
    -rw-r--r-- 1 monsterdev monsterdev   2364 Jun  3 13:37 input.h
    -rw-r--r-- 1 monsterdev monsterdev   5581 Jun  3 13:37 insn-constants.h
    -rw-r--r-- 1 monsterdev monsterdev 208189 Jun  3 13:37 insn-flags.h
    -rw-r--r-- 1 monsterdev monsterdev   6474 Jun  3 13:37 insn-modes.h
    -rw-r--r-- 1 monsterdev monsterdev   2820 Jun  3 13:37 insn-notes.def
    -rw-r--r-- 1 monsterdev monsterdev   1860 Jun  3 13:37 intl.h
    -rw-r--r-- 1 monsterdev monsterdev  18131 Jun  3 13:37 ipa-prop.h
    -rw-r--r-- 1 monsterdev monsterdev   1211 Jun  3 13:37 ipa-reference.h
    -rw-r--r-- 1 monsterdev monsterdev   1290 Jun  3 13:37 ipa-utils.h
    -rw-r--r-- 1 monsterdev monsterdev  18745 Jun  3 13:37 langhooks.h
    -rw-r--r-- 1 monsterdev monsterdev  23878 Jun  3 13:37 libiberty.h
    -rw-r--r-- 1 monsterdev monsterdev   7779 Jun  3 13:37 line-map.h
    -rw-r--r-- 1 monsterdev monsterdev  10060 Jun  3 13:37 machmode.h
    -rw-r--r-- 1 monsterdev monsterdev   5172 Jun  3 13:37 md5.h
    -rw-r--r-- 1 monsterdev monsterdev   1868 Jun  3 13:37 mode-classes.def
    -rw-r--r-- 1 monsterdev monsterdev  20896 Jun  3 13:37 obstack.h
    -rw-r--r-- 1 monsterdev monsterdev   9707 Jun  3 13:37 omp-builtins.def
    -rw-r--r-- 1 monsterdev monsterdev  76885 Jun  3 13:37 options.h
    -rw-r--r-- 1 monsterdev monsterdev   3825 Jun  3 13:37 opts.h
    -rw-r--r-- 1 monsterdev monsterdev  25868 Jun  3 13:37 output.h
    -rw-r--r-- 1 monsterdev monsterdev  31011 Jun  3 13:37 params.def
    -rw-r--r-- 1 monsterdev monsterdev   6218 Jun  3 13:37 params.h
    -rw-r--r-- 1 monsterdev monsterdev   2831 Jun  3 13:37 partition.h
    -rw-r--r-- 1 monsterdev monsterdev   2728 Jun  3 13:37 plugin.def
    -rw-r--r-- 1 monsterdev monsterdev   1398 Jun  3 13:37 plugin.h
    -rw-r--r-- 1 monsterdev monsterdev    395 Jun  3 13:37 plugin-version.h
    -rw-r--r-- 1 monsterdev monsterdev   1563 Jun  3 13:37 pointer-set.h
    -rw-r--r-- 1 monsterdev monsterdev   5050 Jun  3 13:37 predict.def
    -rw-r--r-- 1 monsterdev monsterdev   1453 Jun  3 13:37 predict.h
    -rw-r--r-- 1 monsterdev monsterdev   1123 Jun  3 13:37 prefix.h
    -rw-r--r-- 1 monsterdev monsterdev  13827 Jun  3 13:37 pretty-print.h
    -rw-r--r-- 1 monsterdev monsterdev  19260 Jun  3 13:37 real.h
    -rw-r--r-- 1 monsterdev monsterdev   8343 Jun  3 13:37 reg-notes.def
    -rw-r--r-- 1 monsterdev monsterdev  56027 Jun  3 13:37 rtl.def
    -rw-r--r-- 1 monsterdev monsterdev  94996 Jun  3 13:37 rtl.h
    -rw-r--r-- 1 monsterdev monsterdev   5643 Jun  3 13:37 safe-ctype.h
    -rw-r--r-- 1 monsterdev monsterdev   9401 Jun  3 13:37 sbitmap.h
    -rw-r--r-- 1 monsterdev monsterdev   5503 Jun  3 13:37 splay-tree.h
    -rw-r--r-- 1 monsterdev monsterdev   1918 Jun  3 13:37 statistics.h
    -rw-r--r-- 1 monsterdev monsterdev   3461 Jun  3 13:37 symtab.h
    -rw-r--r-- 1 monsterdev monsterdev  12225 Jun  3 13:37 sync-builtins.def
    -rw-r--r-- 1 monsterdev monsterdev  27805 Jun  3 13:37 system.h
    -rw-r--r-- 1 monsterdev monsterdev  53910 Jun  3 13:37 target.h
    -rw-r--r-- 1 monsterdev monsterdev  11272 Jun  3 13:37 timevar.def
    -rw-r--r-- 1 monsterdev monsterdev   3426 Jun  3 13:37 timevar.h
    -rw-r--r-- 1 monsterdev monsterdev    565 Jun  3 13:37 tm.h
    -rw-r--r-- 1 monsterdev monsterdev    144 Jun  3 13:37 tm_p.h
    -rw-r--r-- 1 monsterdev monsterdev   9335 Jun  3 13:37 tm-preds.h
    -rw-r--r-- 1 monsterdev monsterdev   8178 Jun  3 13:37 toplev.h
    -rw-r--r-- 1 monsterdev monsterdev  15767 Jun  3 13:37 tree-check.h
    -rw-r--r-- 1 monsterdev monsterdev  56086 Jun  3 13:37 tree.def
    -rw-r--r-- 1 monsterdev monsterdev   3180 Jun  3 13:37 tree-dump.h
    -rw-r--r-- 1 monsterdev monsterdev  33260 Jun  3 13:37 tree-flow.h
    -rw-r--r-- 1 monsterdev monsterdev  32003 Jun  3 13:37 tree-flow-inline.h
    -rw-r--r-- 1 monsterdev monsterdev 212167 Jun  3 13:37 tree.h
    -rw-r--r-- 1 monsterdev monsterdev   6166 Jun  3 13:37 tree-inline.h
    -rw-r--r-- 1 monsterdev monsterdev   3115 Jun  3 13:37 tree-iterator.h
    -rw-r--r-- 1 monsterdev monsterdev  25381 Jun  3 13:37 tree-pass.h
    -rw-r--r-- 1 monsterdev monsterdev   4793 Jun  3 13:37 tree-ssa-alias.h
    -rw-r--r-- 1 monsterdev monsterdev   8879 Jun  3 13:37 tree-ssa-operands.h
    -rw-r--r-- 1 monsterdev monsterdev   7170 Jun  3 13:37 tree-ssa-sccvn.h
    -rw-r--r-- 1 monsterdev monsterdev   2584 Jun  3 13:37 treestruct.def
    -rw-r--r-- 1 monsterdev monsterdev  12722 Jun  3 13:37 varray.h
    -rw-r--r-- 1 monsterdev monsterdev  46918 Jun  3 13:37 vec.h
    -rw-r--r-- 1 monsterdev monsterdev   1043 Jun  3 13:37 vecprim.h
    -rw-r--r-- 1 monsterdev monsterdev    184 Jun  3 13:37 version.h
    
    local/lib/gcc/x86_64-pc-os/4.5.0/plugin/include/config:
    total 92
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwxrwxr-x 4 monsterdev monsterdev 20480 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev  2277 Jun  3 13:37 dbxelf.h
    -rw-r--r-- 1 monsterdev monsterdev 18905 Jun  3 13:37 elfos.h
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:37 i386
    -rw-r--r-- 1 monsterdev monsterdev   359 Jun  3 13:37 os.h
    -rw-r--r-- 1 monsterdev monsterdev  1472 Jun  3 13:37 vxworks-dummy.h
    
    local/lib/gcc/x86_64-pc-os/4.5.0/plugin/include/config/i386:
    total 196
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev  3210 Jun  3 13:37 att.h
    -rw-r--r-- 1 monsterdev monsterdev  1277 Jun  3 13:37 biarch64.h
    -rw-r--r-- 1 monsterdev monsterdev  4504 Jun  3 13:37 i386elf.h
    -rw-r--r-- 1 monsterdev monsterdev 95158 Jun  3 13:37 i386.h
    -rw-r--r-- 1 monsterdev monsterdev 12024 Jun  3 13:37 i386-protos.h
    -rw-r--r-- 1 monsterdev monsterdev  2915 Jun  3 13:37 unix.h
    -rw-r--r-- 1 monsterdev monsterdev  3548 Jun  3 13:37 x86-64.h
    
    local/lib/gcc/x86_64-pc-os/4.5.0/plugin/include/cp:
    total 312
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:37 .
    drwxrwxr-x 4 monsterdev monsterdev  20480 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev  20339 Jun  3 13:37 cp-tree.def
    -rw-r--r-- 1 monsterdev monsterdev 220202 Jun  3 13:37 cp-tree.h
    -rw-r--r-- 1 monsterdev monsterdev   3012 Jun  3 13:37 cxx-pretty-print.h
    -rw-r--r-- 1 monsterdev monsterdev  13647 Jun  3 13:37 name-lookup.h
    
    local/libexec:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 8 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 gcc
    
    local/libexec/gcc:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 x86_64-pc-os
    
    local/libexec/gcc/x86_64-pc-os:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:37 4.5.0
    
    local/libexec/gcc/x86_64-pc-os/4.5.0:
    total 142872
    drwxrwxr-x 3 monsterdev monsterdev     4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev     4096 Jun  3 13:37 ..
    -rwxr-xr-x 1 monsterdev monsterdev 46689506 Jun  3 13:37 cc1
    -rwxr-xr-x 1 monsterdev monsterdev 50244139 Jun  3 13:37 cc1plus
    -rwxr-xr-x 1 monsterdev monsterdev   524450 Jun  3 13:37 collect2
    -rwxr-xr-x 1 monsterdev monsterdev 48660909 Jun  3 13:37 f951
    drwxrwxr-x 2 monsterdev monsterdev     4096 Jun  3 13:37 install-tools
    -rwxr-xr-x 1 monsterdev monsterdev   117476 Jun  3 13:37 lto-wrapper
    
    local/libexec/gcc/x86_64-pc-os/4.5.0/install-tools:
    total 476
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:37 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:37 ..
    -rwxr-xr-x 1 monsterdev monsterdev 421281 Jun  3 13:37 fixincl
    -rwxr-xr-x 1 monsterdev monsterdev  13524 Jun  3 13:37 fixinc.sh
    -rwxr-xr-x 1 monsterdev monsterdev   3180 Jun  3 13:37 mkheaders
    -rwxr-xr-x 1 monsterdev monsterdev   3538 Jun  3 13:37 mkinstalldirs
    
    local/share:
    total 24
    drwxrwxr-x  6 monsterdev monsterdev 4096 Jun  3 13:24 .
    drwxrwxr-x  8 monsterdev monsterdev 4096 Jun  3 13:37 ..
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:24 doc
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:39 info
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 locale
    drwxrwxr-x  4 monsterdev monsterdev 4096 Jun  3 13:37 man
    
    local/share/doc:
    total 12
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:24 .
    drwxrwxr-x 6 monsterdev monsterdev 4096 Jun  3 13:24 ..
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:24 mpfr
    
    local/share/doc/mpfr:
    total 172
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:24 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:24 ..
    -rw-r--r-- 1 monsterdev monsterdev   789 Jun  3 13:24 AUTHORS
    -rw-r--r-- 1 monsterdev monsterdev  3313 Jun  3 13:24 BUGS
    -rw-r--r-- 1 monsterdev monsterdev 18013 Jun  3 13:24 COPYING
    -rw-r--r-- 1 monsterdev monsterdev 26440 Jun  3 13:24 COPYING.LIB
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:24 examples
    -rw-r--r-- 1 monsterdev monsterdev 16213 Jun  3 13:24 FAQ.html
    -rw-r--r-- 1 monsterdev monsterdev 11337 Jun  3 13:24 NEWS
    -rw-r--r-- 1 monsterdev monsterdev 18708 Jun  3 13:24 TODO
    
    local/share/doc/mpfr/examples:
    total 56
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:24 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:24 ..
    -rw-r--r-- 1 monsterdev monsterdev 2976 Jun  3 13:24 divworst.c
    -rw-r--r-- 1 monsterdev monsterdev   41 Jun  3 13:24 ReadMe
    -rw-r--r-- 1 monsterdev monsterdev 2592 Jun  3 13:24 rndo-add.c
    -rw-r--r-- 1 monsterdev monsterdev 1653 Jun  3 13:24 sample.c
    
    local/share/info:
    total 8388
    drwxrwxr-x 2 monsterdev monsterdev    4096 Jun  3 13:39 .
    drwxrwxr-x 6 monsterdev monsterdev    4096 Jun  3 13:24 ..
    -rw-r--r-- 1 monsterdev monsterdev  872781 Jun  3 13:19 as.info
    -rw-r--r-- 1 monsterdev monsterdev  481845 Jun  3 13:19 bfd.info
    -rw-r--r-- 1 monsterdev monsterdev  182154 Jun  3 13:19 binutils.info
    -rw-r--r-- 1 monsterdev monsterdev  116438 Jun  3 13:39 configure.info
    -rw-r--r-- 1 monsterdev monsterdev  234494 Jun  3 13:37 cpp.info
    -rw-r--r-- 1 monsterdev monsterdev   50224 Jun  3 13:37 cppinternals.info
    -rw-rw-r-- 1 monsterdev monsterdev    3606 Jun  3 13:37 dir
    -rw-r--r-- 1 monsterdev monsterdev 2023532 Jun  3 13:37 gcc.info
    -rw-r--r-- 1 monsterdev monsterdev  195562 Jun  3 13:37 gccinstall.info
    -rw-r--r-- 1 monsterdev monsterdev 2221774 Jun  3 13:37 gccint.info
    -rw-r--r-- 1 monsterdev monsterdev  583648 Jun  3 13:37 gfortran.info
    -rw-r--r-- 1 monsterdev monsterdev    6003 Jun  3 13:22 gmp.info
    -rw-r--r-- 1 monsterdev monsterdev  300864 Jun  3 13:22 gmp.info-1
    -rw-r--r-- 1 monsterdev monsterdev  191075 Jun  3 13:22 gmp.info-2
    -rw-r--r-- 1 monsterdev monsterdev  112301 Jun  3 13:19 gprof.info
    -rw-r--r-- 1 monsterdev monsterdev  350880 Jun  3 13:19 ld.info
    -rw-r--r-- 1 monsterdev monsterdev   57630 Jun  3 13:24 mpc.info
    -rw-r--r-- 1 monsterdev monsterdev  182757 Jun  3 13:24 mpfr.info
    -rw-r--r-- 1 monsterdev monsterdev  215742 Jun  3 13:39 standards.info
    
    local/share/locale:
    total 92
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x  6 monsterdev monsterdev 4096 Jun  3 13:24 ..
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 da
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 de
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 es
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 fi
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 fr
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 ga
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 id
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 ja
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 ms
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 nl
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 pt_BR
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 ro
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 ru
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 rw
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 sk
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 sv
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 tr
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 uk
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 vi
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 zh_CN
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 zh_TW
    
    local/share/locale/da:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/da/LC_MESSAGES:
    total 240
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 60556 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 67752 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  9586 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 40607 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  8332 Jun  3 13:19 opcodes.mo
    
    local/share/locale/de:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/de/LC_MESSAGES:
    total 56
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 10545 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 16919 Jun  3 13:19 opcodes.mo
    
    local/share/locale/es:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/es/LC_MESSAGES:
    total 816
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 109357 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 163294 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev 403734 Jun  3 13:19 gas.mo
    -rw-r--r-- 1 monsterdev monsterdev  10797 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  55441 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  26049 Jun  3 13:19 opcodes.mo
    
    local/share/locale/fi:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/fi/LC_MESSAGES:
    total 396
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 111132 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 140922 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  11021 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  55207 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  26801 Jun  3 13:19 opcodes.mo
    
    local/share/locale/fr:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/fr/LC_MESSAGES:
    total 576
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev  71749 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 134234 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev 228353 Jun  3 13:19 gas.mo
    -rw-r--r-- 1 monsterdev monsterdev  10838 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  51807 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  25584 Jun  3 13:19 opcodes.mo
    
    local/share/locale/ga:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/ga/LC_MESSAGES:
    total 116
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 10440 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 48922 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev 24028 Jun  3 13:19 opcodes.mo
    
    local/share/locale/id:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/id/LC_MESSAGES:
    total 740
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev  97793 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 146604 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev 362768 Jun  3 13:19 gas.mo
    -rw-r--r-- 1 monsterdev monsterdev  10387 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  49548 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  23690 Jun  3 13:19 opcodes.mo
    
    local/share/locale/ja:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/ja/LC_MESSAGES:
    total 160
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 38616 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 97376 Jun  3 13:19 binutils.mo
    
    local/share/locale/ms:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/ms/LC_MESSAGES:
    total 28
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 10360 Jun  3 13:19 gprof.mo
    
    local/share/locale/nl:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/nl/LC_MESSAGES:
    total 64
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 10712 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 25505 Jun  3 13:19 opcodes.mo
    
    local/share/locale/pt_BR:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/pt_BR/LC_MESSAGES:
    total 48
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 9984 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 8467 Jun  3 13:19 opcodes.mo
    
    local/share/locale/ro:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/ro/LC_MESSAGES:
    total 156
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 69038 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 20265 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  9898 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev 15986 Jun  3 13:19 opcodes.mo
    
    local/share/locale/ru:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/ru/LC_MESSAGES:
    total 324
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 128466 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 173223 Jun  3 13:19 binutils.mo
    
    local/share/locale/rw:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/rw/LC_MESSAGES:
    total 56
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev  429 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev  615 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  396 Jun  3 13:19 gas.mo
    -rw-r--r-- 1 monsterdev monsterdev  486 Jun  3 13:19 gprof.mo
    
    local/share/locale/sk:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/sk/LC_MESSAGES:
    total 164
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 149635 Jun  3 13:19 binutils.mo
    
    local/share/locale/sv:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/sv/LC_MESSAGES:
    total 300
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev  67266 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 113208 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  10367 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  43131 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  16004 Jun  3 13:19 opcodes.mo
    
    local/share/locale/tr:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/tr/LC_MESSAGES:
    total 540
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev  69529 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 129842 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev 220920 Jun  3 13:19 gas.mo
    -rw-r--r-- 1 monsterdev monsterdev  11331 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  41339 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  16094 Jun  3 13:19 opcodes.mo
    
    local/share/locale/uk:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/uk/LC_MESSAGES:
    total 188
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 172392 Jun  3 13:19 binutils.mo
    
    local/share/locale/vi:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/vi/LC_MESSAGES:
    total 440
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 118338 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 172787 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  12435 Jun  3 13:19 gprof.mo
    -rw-r--r-- 1 monsterdev monsterdev  59342 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  27676 Jun  3 13:19 opcodes.mo
    
    local/share/locale/zh_CN:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/zh_CN/LC_MESSAGES:
    total 184
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 28132 Jun  3 13:19 bfd.mo
    -rw-r--r-- 1 monsterdev monsterdev 75903 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev 24796 Jun  3 13:19 ld.mo
    -rw-r--r-- 1 monsterdev monsterdev  9050 Jun  3 13:19 opcodes.mo
    
    local/share/locale/zh_TW:
    total 12
    drwxrwxr-x  3 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 23 monsterdev monsterdev 4096 Jun  3 13:19 ..
    drwxrwxr-x  2 monsterdev monsterdev 4096 Jun  3 13:19 LC_MESSAGES
    
    local/share/locale/zh_TW/LC_MESSAGES:
    total 188
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev   4096 Jun  3 13:19 ..
    -rw-r--r-- 1 monsterdev monsterdev 121475 Jun  3 13:19 binutils.mo
    -rw-r--r-- 1 monsterdev monsterdev  44839 Jun  3 13:19 ld.mo
    
    local/share/man:
    total 16
    drwxrwxr-x 4 monsterdev monsterdev 4096 Jun  3 13:37 .
    drwxrwxr-x 6 monsterdev monsterdev 4096 Jun  3 13:24 ..
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 man1
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:37 man7
    
    local/share/man/man1:
    total 2236
    drwxrwxr-x 2 monsterdev monsterdev   4096 Jun  3 13:37 .
    drwxrwxr-x 4 monsterdev monsterdev   4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev   9270 Jun  3 13:19 x86_64-pc-os-addr2line.1
    -rw-r--r-- 1 monsterdev monsterdev  17270 Jun  3 13:19 x86_64-pc-os-ar.1
    -rw-r--r-- 1 monsterdev monsterdev  45604 Jun  3 13:19 x86_64-pc-os-as.1
    -rw-r--r-- 1 monsterdev monsterdev  11059 Jun  3 13:19 x86_64-pc-os-c++filt.1
    -rw-r--r-- 1 monsterdev monsterdev  40942 Jun  3 13:37 x86_64-pc-os-cpp.1
    -rw-r--r-- 1 monsterdev monsterdev  20220 Jun  3 13:19 x86_64-pc-os-dlltool.1
    -rw-r--r-- 1 monsterdev monsterdev 752752 Jun  3 13:37 x86_64-pc-os-g++.1
    -rw-r--r-- 1 monsterdev monsterdev 752752 Jun  3 13:37 x86_64-pc-os-gcc.1
    -rw-r--r-- 1 monsterdev monsterdev  24421 Jun  3 13:37 x86_64-pc-os-gcov.1
    -rw-r--r-- 1 monsterdev monsterdev  57834 Jun  3 13:37 x86_64-pc-os-gfortran.1
    -rw-r--r-- 1 monsterdev monsterdev  29869 Jun  3 13:19 x86_64-pc-os-gprof.1
    -rw-r--r-- 1 monsterdev monsterdev 106571 Jun  3 13:19 x86_64-pc-os-ld.1
    -rw-r--r-- 1 monsterdev monsterdev   8374 Jun  3 13:19 x86_64-pc-os-nlmconv.1
    -rw-r--r-- 1 monsterdev monsterdev  17141 Jun  3 13:19 x86_64-pc-os-nm.1
    -rw-r--r-- 1 monsterdev monsterdev  40880 Jun  3 13:19 x86_64-pc-os-objcopy.1
    -rw-r--r-- 1 monsterdev monsterdev  29956 Jun  3 13:19 x86_64-pc-os-objdump.1
    -rw-r--r-- 1 monsterdev monsterdev   6280 Jun  3 13:19 x86_64-pc-os-ranlib.1
    -rw-r--r-- 1 monsterdev monsterdev  13465 Jun  3 13:19 x86_64-pc-os-readelf.1
    -rw-r--r-- 1 monsterdev monsterdev   8969 Jun  3 13:19 x86_64-pc-os-size.1
    -rw-r--r-- 1 monsterdev monsterdev   8683 Jun  3 13:19 x86_64-pc-os-strings.1
    -rw-r--r-- 1 monsterdev monsterdev  13708 Jun  3 13:19 x86_64-pc-os-strip.1
    -rw-r--r-- 1 monsterdev monsterdev  10630 Jun  3 13:19 x86_64-pc-os-windmc.1
    -rw-r--r-- 1 monsterdev monsterdev  12997 Jun  3 13:19 x86_64-pc-os-windres.1
    
    local/share/man/man7:
    total 112
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:37 .
    drwxrwxr-x 4 monsterdev monsterdev  4096 Jun  3 13:37 ..
    -rw-r--r-- 1 monsterdev monsterdev  6520 Jun  3 13:37 fsf-funding.7
    -rw-r--r-- 1 monsterdev monsterdev 26591 Jun  3 13:37 gfdl.7
    -rw-r--r-- 1 monsterdev monsterdev 42579 Jun  3 13:37 gpl.7
    
    local/x86_64-pc-os:
    total 28
    drwxrwxr-x 5 monsterdev monsterdev  4096 Jun  3 13:39 .
    drwxrwxr-x 8 monsterdev monsterdev  4096 Jun  3 13:37 ..
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:37 bin
    drwxrwxr-x 5 monsterdev monsterdev 12288 Jun  3 13:39 include
    drwxrwxr-x 3 monsterdev monsterdev  4096 Jun  3 13:39 lib
    
    local/x86_64-pc-os/bin:
    total 34072
    drwxrwxr-x 2 monsterdev monsterdev    4096 Jun  3 13:37 .
    drwxrwxr-x 5 monsterdev monsterdev    4096 Jun  3 13:39 ..
    -rwxr-xr-x 2 monsterdev monsterdev 3385257 Jun  3 13:19 ar
    -rwxr-xr-x 2 monsterdev monsterdev 4872363 Jun  3 13:19 as
    -rwxr-xr-x 2 monsterdev monsterdev  669352 Jun  3 13:37 c++
    -rwxr-xr-x 2 monsterdev monsterdev  669352 Jun  3 13:37 g++
    -rwxr-xr-x 1 monsterdev monsterdev  664501 Jun  3 13:37 gcc
    -rwxr-xr-x 1 monsterdev monsterdev  677072 Jun  3 13:37 gfortran
    -rwxr-xr-x 2 monsterdev monsterdev 4255437 Jun  3 13:19 ld
    -rwxr-xr-x 2 monsterdev monsterdev 3273292 Jun  3 13:19 nm
    -rwxr-xr-x 2 monsterdev monsterdev 4032399 Jun  3 13:19 objcopy
    -rwxr-xr-x 2 monsterdev monsterdev 4840114 Jun  3 13:19 objdump
    -rwxr-xr-x 2 monsterdev monsterdev 3385248 Jun  3 13:19 ranlib
    -rwxr-xr-x 2 monsterdev monsterdev 4032390 Jun  3 13:19 strip
    
    local/x86_64-pc-os/include:
    total 752
    drwxrwxr-x 5 monsterdev monsterdev 12288 Jun  3 13:39 .
    drwxrwxr-x 5 monsterdev monsterdev  4096 Jun  3 13:39 ..
    -rw-r--r-- 1 monsterdev monsterdev   420 Jun  3 13:39 alloca.h
    -rw-r--r-- 1 monsterdev monsterdev  4002 Jun  3 13:39 _ansi.h
    -rw-r--r-- 1 monsterdev monsterdev  1337 Jun  3 13:39 argz.h
    -rw-r--r-- 1 monsterdev monsterdev  2958 Jun  3 13:39 ar.h
    -rw-r--r-- 1 monsterdev monsterdev  1088 Jun  3 13:39 assert.h
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 bits
    -rw-r--r-- 1 monsterdev monsterdev  3819 Jun  3 13:39 ctype.h
    -rw-r--r-- 1 monsterdev monsterdev   234 Jun  3 13:39 dirent.h
    -rw-r--r-- 1 monsterdev monsterdev   366 Jun  3 13:39 envlock.h
    -rw-r--r-- 1 monsterdev monsterdev   781 Jun  3 13:39 envz.h
    -rw-r--r-- 1 monsterdev monsterdev   174 Jun  3 13:39 errno.h
    -rw-r--r-- 1 monsterdev monsterdev   185 Jun  3 13:39 fastmath.h
    -rw-r--r-- 1 monsterdev monsterdev    23 Jun  3 13:39 fcntl.h
    -rw-r--r-- 1 monsterdev monsterdev  2385 Jun  3 13:39 fnmatch.h
    -rw-r--r-- 1 monsterdev monsterdev  6622 Jun  3 13:39 getopt.h
    -rw-r--r-- 1 monsterdev monsterdev  3764 Jun  3 13:39 glob.h
    -rw-r--r-- 1 monsterdev monsterdev  3385 Jun  3 13:39 grp.h
    -rw-r--r-- 1 monsterdev monsterdev  2130 Jun  3 13:39 iconv.h
    -rw-r--r-- 1 monsterdev monsterdev  5359 Jun  3 13:39 ieeefp.h
    -rw-r--r-- 1 monsterdev monsterdev  6714 Jun  3 13:39 inttypes.h
    -rw-r--r-- 1 monsterdev monsterdev  4510 Jun  3 13:39 langinfo.h
    -rw-r--r-- 1 monsterdev monsterdev   300 Jun  3 13:39 libgen.h
    -rw-r--r-- 1 monsterdev monsterdev  3936 Jun  3 13:39 limits.h
    -rw-r--r-- 1 monsterdev monsterdev  1265 Jun  3 13:39 locale.h
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 machine
    -rw-r--r-- 1 monsterdev monsterdev  4292 Jun  3 13:39 malloc.h
    -rw-r--r-- 1 monsterdev monsterdev 18669 Jun  3 13:39 math.h
    -rw-r--r-- 1 monsterdev monsterdev  5965 Jun  3 13:39 newlib.h
    -rw-r--r-- 1 monsterdev monsterdev   121 Jun  3 13:39 paths.h
    -rw-r--r-- 1 monsterdev monsterdev  1511 Jun  3 13:39 process.h
    -rw-r--r-- 1 monsterdev monsterdev 11953 Jun  3 13:39 pthread.h
    -rw-r--r-- 1 monsterdev monsterdev  2841 Jun  3 13:39 pwd.h
    -rw-r--r-- 1 monsterdev monsterdev  8670 Jun  3 13:39 reent.h
    -rw-r--r-- 1 monsterdev monsterdev   220 Jun  3 13:39 regdef.h
    -rw-r--r-- 1 monsterdev monsterdev  3489 Jun  3 13:39 regex.h
    -rw-r--r-- 1 monsterdev monsterdev   153 Jun  3 13:39 sched.h
    -rw-r--r-- 1 monsterdev monsterdev  1286 Jun  3 13:39 search.h
    -rw-r--r-- 1 monsterdev monsterdev   269 Jun  3 13:39 setjmp.h
    -rw-r--r-- 1 monsterdev monsterdev   601 Jun  3 13:39 signal.h
    -rw-r--r-- 1 monsterdev monsterdev 12251 Jun  3 13:39 stdint.h
    -rw-r--r-- 1 monsterdev monsterdev 27404 Jun  3 13:39 stdio.h
    -rw-r--r-- 1 monsterdev monsterdev  7954 Jun  3 13:39 stdlib.h
    -rw-r--r-- 1 monsterdev monsterdev  3229 Jun  3 13:39 string.h
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 sys
    -rw-r--r-- 1 monsterdev monsterdev  1170 Jun  3 13:39 _syslist.h
    -rw-r--r-- 1 monsterdev monsterdev  1309 Jun  3 13:39 tar.h
    -rw-r--r-- 1 monsterdev monsterdev    92 Jun  3 13:39 termios.h
    -rw-r--r-- 1 monsterdev monsterdev  6644 Jun  3 13:39 time.h
    -rw-r--r-- 1 monsterdev monsterdev  2178 Jun  3 13:39 unctrl.h
    -rw-r--r-- 1 monsterdev monsterdev    89 Jun  3 13:39 unistd.h
    -rw-r--r-- 1 monsterdev monsterdev   185 Jun  3 13:39 utime.h
    -rw-r--r-- 1 monsterdev monsterdev    90 Jun  3 13:39 utmp.h
    -rw-r--r-- 1 monsterdev monsterdev  8021 Jun  3 13:39 wchar.h
    -rw-r--r-- 1 monsterdev monsterdev   988 Jun  3 13:39 wctype.h
    -rw-r--r-- 1 monsterdev monsterdev  1431 Jun  3 13:39 wordexp.h
    
    local/x86_64-pc-os/include/bits:
    total 16
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 .
    drwxrwxr-x 5 monsterdev monsterdev 12288 Jun  3 13:39 ..
    
    local/x86_64-pc-os/include/machine:
    total 192
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 .
    drwxrwxr-x 5 monsterdev monsterdev 12288 Jun  3 13:39 ..
    -rw-r--r-- 1 monsterdev monsterdev    48 Jun  3 13:39 ansi.h
    -rw-r--r-- 1 monsterdev monsterdev  3031 Jun  3 13:39 _default_types.h
    -rw-r--r-- 1 monsterdev monsterdev   327 Jun  3 13:39 endian.h
    -rw-r--r-- 1 monsterdev monsterdev  2829 Jun  3 13:39 fastmath.h
    -rw-r--r-- 1 monsterdev monsterdev  7526 Jun  3 13:39 ieeefp.h
    -rw-r--r-- 1 monsterdev monsterdev   138 Jun  3 13:39 malloc.h
    -rw-r--r-- 1 monsterdev monsterdev    50 Jun  3 13:39 param.h
    -rw-r--r-- 1 monsterdev monsterdev   932 Jun  3 13:39 setjmp-dj.h
    -rw-r--r-- 1 monsterdev monsterdev  6356 Jun  3 13:39 setjmp.h
    -rw-r--r-- 1 monsterdev monsterdev   138 Jun  3 13:39 stdlib.h
    -rw-r--r-- 1 monsterdev monsterdev    29 Jun  3 13:39 termios.h
    -rw-r--r-- 1 monsterdev monsterdev   375 Jun  3 13:39 time.h
    -rw-r--r-- 1 monsterdev monsterdev   162 Jun  3 13:39 _types.h
    -rw-r--r-- 1 monsterdev monsterdev   667 Jun  3 13:39 types.h
    
    local/x86_64-pc-os/include/sys:
    total 460
    drwxrwxr-x 2 monsterdev monsterdev  4096 Jun  3 13:39 .
    drwxrwxr-x 5 monsterdev monsterdev 12288 Jun  3 13:39 ..
    -rw-r--r-- 1 monsterdev monsterdev  4315 Jun  3 13:39 cdefs.h
    -rw-r--r-- 1 monsterdev monsterdev  5808 Jun  3 13:39 config.h
    -rw-r--r-- 1 monsterdev monsterdev    50 Jun  3 13:39 custom_file.h
    -rw-r--r-- 1 monsterdev monsterdev  6416 Jun  3 13:39 _default_fcntl.h
    -rw-r--r-- 1 monsterdev monsterdev   395 Jun  3 13:39 dirent.h
    -rw-r--r-- 1 monsterdev monsterdev  7317 Jun  3 13:39 errno.h
    -rw-r--r-- 1 monsterdev monsterdev    83 Jun  3 13:39 fcntl.h
    -rw-r--r-- 1 monsterdev monsterdev  6349 Jun  3 13:39 features.h
    -rw-r--r-- 1 monsterdev monsterdev    24 Jun  3 13:39 file.h
    -rw-r--r-- 1 monsterdev monsterdev  2794 Jun  3 13:39 iconvnls.h
    -rw-r--r-- 1 monsterdev monsterdev   805 Jun  3 13:39 lock.h
    -rw-r--r-- 1 monsterdev monsterdev   508 Jun  3 13:39 param.h
    -rw-r--r-- 1 monsterdev monsterdev 15264 Jun  3 13:39 queue.h
    -rw-r--r-- 1 monsterdev monsterdev 26642 Jun  3 13:39 reent.h
    -rw-r--r-- 1 monsterdev monsterdev   307 Jun  3 13:39 resource.h
    -rw-r--r-- 1 monsterdev monsterdev  1823 Jun  3 13:39 sched.h
    -rw-r--r-- 1 monsterdev monsterdev 10471 Jun  3 13:39 signal.h
    -rw-r--r-- 1 monsterdev monsterdev  5282 Jun  3 13:39 stat.h
    -rw-r--r-- 1 monsterdev monsterdev   807 Jun  3 13:39 stdio.h
    -rw-r--r-- 1 monsterdev monsterdev   116 Jun  3 13:39 string.h
    -rw-r--r-- 1 monsterdev monsterdev  3211 Jun  3 13:39 syslimits.h
    -rw-r--r-- 1 monsterdev monsterdev   752 Jun  3 13:39 timeb.h
    -rw-r--r-- 1 monsterdev monsterdev  2430 Jun  3 13:39 time.h
    -rw-r--r-- 1 monsterdev monsterdev   548 Jun  3 13:39 times.h
    -rw-r--r-- 1 monsterdev monsterdev  1822 Jun  3 13:39 _types.h
    -rw-r--r-- 1 monsterdev monsterdev 15873 Jun  3 13:39 types.h
    -rw-r--r-- 1 monsterdev monsterdev 20434 Jun  3 13:39 unistd.h
    -rw-r--r-- 1 monsterdev monsterdev   363 Jun  3 13:39 utime.h
    -rw-r--r-- 1 monsterdev monsterdev   937 Jun  3 13:39 wait.h
    
    local/x86_64-pc-os/lib:
    total 12192
    drwxrwxr-x 3 monsterdev monsterdev    4096 Jun  3 13:39 .
    drwxrwxr-x 5 monsterdev monsterdev    4096 Jun  3 13:39 ..
    -rw-r--r-- 1 monsterdev monsterdev    4248 Jun  3 13:39 crt0.o
    drwxrwxr-x 2 monsterdev monsterdev    4096 Jun  3 13:19 ldscripts
    -rw-r--r-- 2 monsterdev monsterdev 5332636 Jun  3 13:39 libc.a
    -rw-r--r-- 2 monsterdev monsterdev 5332636 Jun  3 13:39 libg.a
    -rw-r--r-- 1 monsterdev monsterdev 1652398 Jun  3 13:39 libm.a
    -rwxr-xr-x 1 monsterdev monsterdev   99040 Jun  3 13:39 libnosys.a
    
    local/x86_64-pc-os/lib/ldscripts:
    total 168
    drwxrwxr-x 2 monsterdev monsterdev 4096 Jun  3 13:19 .
    drwxrwxr-x 3 monsterdev monsterdev 4096 Jun  3 13:39 ..
    -rw-r--r-- 1 monsterdev monsterdev 7807 Jun  3 13:19 os_x86_64.x
    -rw-r--r-- 1 monsterdev monsterdev 7590 Jun  3 13:19 os_x86_64.xbn
    -rw-r--r-- 1 monsterdev monsterdev 7579 Jun  3 13:19 os_x86_64.xc
    -rw-r--r-- 1 monsterdev monsterdev 7739 Jun  3 13:19 os_x86_64.xd
    -rw-r--r-- 1 monsterdev monsterdev 7528 Jun  3 13:19 os_x86_64.xdc
    -rw-r--r-- 1 monsterdev monsterdev 7518 Jun  3 13:19 os_x86_64.xdw
    -rw-r--r-- 1 monsterdev monsterdev 7807 Jun  3 13:19 os_x86_64.xn
    -rw-r--r-- 1 monsterdev monsterdev 4934 Jun  3 13:19 os_x86_64.xr
    -rw-r--r-- 1 monsterdev monsterdev 4980 Jun  3 13:19 os_x86_64.xu
    -rw-r--r-- 1 monsterdev monsterdev 7569 Jun  3 13:19 os_x86_64.xw
```

---

