---
title: "valgrind returns excessive number of errors"
date: 2010-10-28
forum: Programming Talk
---

### Post by blobhunter on 2010-10-28
Hi,

I am running Ubuntu 10.04 LTS - the Lucid Lynx, and try to keep the system up to date.
I am getting more and more error messages reported by valgrind, and it's gotten to a point now that I can no longer use it. Valgrind just swamps me with false positive error messages. Not exactly sure when it got this bad, but maybe it coincides with upgrading from Ubuntu 9 to 10 (I didn't use valgrind for a while then).

Here are a few examples what I get:

[FONT="Courier New"]==31326== Conditional jump or move depends on uninitialised value(s)
==31326==    at 0x400BAE6: _dl_relocate_object (do-rel.h:65)
==31326==    by 0x4003D32: dl_main (rtld.c:2292)
==31326==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==31326==    by 0x4001386: _dl_start (rtld.c:333)
==31326==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==31326==    by 0x4: ???
...
==31326== Conditional jump or move depends on uninitialised value(s)
==31326==    at 0x5D65064: __GI_strlen (strlen.S:37)
==31326==    by 0x5D7C502: __tzstring (tzset.c:94)
==31326==    by 0x5D7E492: __tzfile_read (tzfile.c:430)
==31326==    by 0x5D7D093: tzset_internal (tzset.c:439)
==31326==    by 0x5D7D1F8: __tz_convert (tzset.c:624)
...
==31326== Invalid read of size 8
==31326==    at 0x5D6362A: __GI_strcmp (strcmp.S:100)
==31326==    by 0x5D7C536: __tzstring (tzset.c:102)
==31326==    by 0x5D7E492: __tzfile_read (tzfile.c:430)
==31326==    by 0x5D7D093: tzset_internal (tzset.c:439)
==31326==    by 0x5D7D1F8: __tz_convert (tzset.c:624)
...
==31326== Conditional jump or move depends on uninitialised value(s)
==31326==    at 0x5D7E526: __tzfile_read (tzfile.c:452)
==31326==    by 0x5D7D093: tzset_internal (tzset.c:439)
==31326==    by 0x5D7D1F8: __tz_convert (tzset.c:624)
[/FONT]

For example, if I compile the following simple program and run it with valgrind, it will complain about strlen:


[FONT="Courier New"]
#include <cstdio>
#include <cstring>

using namespace std;
int main() {
  int length = 9;
  char* line = new char[length+1];
  line[length] = '\0';
  for( int i = 0; i < length; i++ ) {
    line[i] = i+65;
  }
  fprintf(stdout,"Line = '%s'\n", line);

  int size = strlen(line);
  fprintf(stdout,"Size = %d\n", size);
}
[/FONT]

valgrind's output:

[FONT="Courier New"]==31453== Conditional jump or move depends on uninitialised value(s)
==31453==    at 0x400BAE6: _dl_relocate_object (do-rel.h:65)
==31453==    by 0x4003D32: dl_main (rtld.c:2292)
==31453==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==31453==    by 0x4001386: _dl_start (rtld.c:333)
==31453==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==31453== 
==31453== Conditional jump or move depends on uninitialised value(s)
==31453==    at 0x400BAEF: _dl_relocate_object (do-rel.h:68)
==31453==    by 0x4003D32: dl_main (rtld.c:2292)
==31453==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==31453==    by 0x4001386: _dl_start (rtld.c:333)
==31453==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==31453== 
==31453== Invalid read of size 8
==31453==    at 0x565E052: __GI_strlen (strlen.S:31)
==31453==    by 0x400776: main (valgrind_test.cc:15)
==31453==  Address 0x595e038 is 8 bytes inside a block of size 10 alloc'd
==31453==    at 0x4C27BCC: operator new[](unsigned long) (vg_replace_malloc.c:274)
==31453==    by 0x400712: main (valgrind_test.cc:8)
==31453== 
[/FONT]


I've tried to add suppressions but after adding 20 suppressions I gave up because I'm still getting thousands of related messages.

Please help!

---

### Post by dwhitney67 on 2010-10-28
I did not get the valgrind errors you reported on Ubuntu 10.04 LTS.

Thus, it would be helpful if you could share with us how you built the application, and also how you ran it using valgrind.

I did the following:
```

g++ -Wall -pedantic -g foo.cpp
valgrind -v a.out

```

---

### Post by blobhunter on 2010-10-28
I did the same thing:

```
g++ -g valgrind_test.cc -o valgrind_test
valgrind ./valgrind_test > tmp
```


gcc version:

```
g++ -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
``` 

valgrind version:

```
valgrind --version
valgrind-3.4.1
```


As I said, I didn't have these problems before. It started about a year ago, and got worse over time. Surely it must have to do with all the updates that I did over time, of the Ubuntu system etc..

---

### Post by blobhunter on 2010-10-28
And by the way, here is the full output when I turn on the valgrind verbose option:

```
valgrind -v ./valgrind_test > tmp

==3900== Memcheck, a memory error detector.
==3900== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.
==3900== Using LibVEX rev 1884, a library for dynamic binary translation.
==3900== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.
==3900== Using valgrind-3.4.1, a dynamic binary instrumentation framework.
==3900== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.
==3900== 
--3900-- Command line
--3900--    ./valgrind_test
--3900-- Startup, with flags:
--3900--    --suppressions=/home/bjorn/valgrind_suppression_file.supp
--3900--    -v
--3900-- Contents of /proc/version:
--3900--   Linux version 2.6.32-23-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010
--3900-- Arch and hwcaps: AMD64, amd64-sse2
--3900-- Page sizes: currently 4096, max supported 4096
--3900-- Valgrind library directory: /usr/local/lib/valgrind
--3900-- Reading syms from /home/bjorn/tmp/valgrind_test (0x400000)
--3900-- Reading syms from /lib/ld-2.11.1.so (0x4000000)
--3900-- Reading debug info from /lib/ld-2.11.1.so ..
--3900-- .. CRC mismatch (computed 88039adb wanted c17ec96b)
--3900-- Reading debug info from /usr/lib/debug/lib/ld-2.11.1.so ..
--3900-- Reading syms from /usr/local/lib/valgrind/amd64-linux/memcheck (0x38000000)
--3900--    object doesn't have a dynamic symbol table
--3900-- Reading suppressions file: /home/bjorn/valgrind_suppression_file.supp
--3900-- Reading suppressions file: /usr/local/lib/valgrind/default.supp
--3900-- Reading syms from /usr/local/lib/valgrind/amd64-linux/vgpreload_core.so (0x4a22000)
--3900-- Reading syms from /usr/local/lib/valgrind/amd64-linux/vgpreload_memcheck.so (0x4c24000)
--3900-- REDIR: 0x4018100 (index) redirected to 0x4c28e40 (index)
--3900-- REDIR: 0x4018180 (strcmp) redirected to 0x4c29400 (strcmp)
--3900-- REDIR: 0x4018290 (strlen) redirected to 0x4c29100 (strlen)
--3900-- Reading syms from /usr/lib/libstdc++.so.6.0.13 (0x4e2d000)
--3900-- Reading debug info from /usr/lib/libstdc++.so.6.0.13 ..
--3900-- .. CRC mismatch (computed 7b5bd5a5 wanted e2f63673)
--3900--    object doesn't have a symbol table
--3900-- Reading syms from /lib/libm-2.11.1.so (0x5141000)
--3900-- Reading debug info from /lib/libm-2.11.1.so ..
--3900-- .. CRC mismatch (computed 043548c3 wanted a081b93d)
--3900-- Reading debug info from /usr/lib/debug/lib/libm-2.11.1.so ..
--3900-- Reading syms from /lib/libgcc_s.so.1 (0x53c4000)
--3900-- Reading debug info from /lib/libgcc_s.so.1 ..
--3900-- .. CRC mismatch (computed 7c01dfc9 wanted 9d78e511)
--3900--    object doesn't have a symbol table
--3900-- Reading syms from /lib/libc-2.11.1.so (0x55db000)
--3900-- Reading debug info from /lib/libc-2.11.1.so ..
--3900-- .. CRC mismatch (computed 375e41a0 wanted 405b95a9)
--3900-- Reading debug info from /usr/lib/debug/lib/libc-2.11.1.so ..
==3900== Conditional jump or move depends on uninitialised value(s)
==3900==    at 0x400BAE6: _dl_relocate_object (do-rel.h:65)
==3900==    by 0x4003D32: dl_main (rtld.c:2292)
==3900==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==3900==    by 0x4001386: _dl_start (rtld.c:333)
==3900==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==3900== 
==3900== Conditional jump or move depends on uninitialised value(s)
==3900==    at 0x400BAEF: _dl_relocate_object (do-rel.h:68)
==3900==    by 0x4003D32: dl_main (rtld.c:2292)
==3900==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==3900==    by 0x4001386: _dl_start (rtld.c:333)
==3900==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
--3900-- REDIR: 0x4ef8380 (operator new[](unsigned long)) redirected to 0x4c27b00 (operator new[](unsigned long))
--3900-- REDIR: 0x5663270 (strchrnul) redirected to 0x4c2a010 (strchrnul)
==3900== 
==3900== Invalid read of size 8
==3900==    at 0x565E052: __GI_strlen (strlen.S:31)
==3900==    by 0x400776: main (valgrind_test.cc:15)
==3900==  Address 0x595e038 is 8 bytes inside a block of size 10 alloc'd
==3900==    at 0x4C27BCC: operator new[](unsigned long) (vg_replace_malloc.c:274)
==3900==    by 0x400712: main (valgrind_test.cc:8)
--3900-- REDIR: 0x5658e10 (free) redirected to 0x4c27580 (free)
==3900== 
==3900== ERROR SUMMARY: 3 errors from 3 contexts (suppressed: 0 from 0)
==3900== 
==3900== 1 errors in context 1 of 3:
==3900== Invalid read of size 8
==3900==    at 0x565E052: __GI_strlen (strlen.S:31)
==3900==    by 0x400776: main (valgrind_test.cc:15)
==3900==  Address 0x595e038 is 8 bytes inside a block of size 10 alloc'd
==3900==    at 0x4C27BCC: operator new[](unsigned long) (vg_replace_malloc.c:274)
==3900==    by 0x400712: main (valgrind_test.cc:8)
==3900== 
==3900== 1 errors in context 2 of 3:
==3900== Conditional jump or move depends on uninitialised value(s)
==3900==    at 0x400BAEF: _dl_relocate_object (do-rel.h:68)
==3900==    by 0x4003D32: dl_main (rtld.c:2292)
==3900==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==3900==    by 0x4001386: _dl_start (rtld.c:333)
==3900==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==3900== 
==3900== 1 errors in context 3 of 3:
==3900== Conditional jump or move depends on uninitialised value(s)
==3900==    at 0x400BAE6: _dl_relocate_object (do-rel.h:65)
==3900==    by 0x4003D32: dl_main (rtld.c:2292)
==3900==    by 0x40165C6: _dl_sysdep_start (dl-sysdep.c:243)
==3900==    by 0x4001386: _dl_start (rtld.c:333)
==3900==    by 0x4000AF7: (within /lib/ld-2.11.1.so)
==3900== IN SUMMARY: 3 errors from 3 contexts (suppressed: 0 from 0)
==3900== 
==3900== malloc/free: in use at exit: 10 bytes in 1 blocks.
==3900== malloc/free: 1 allocs, 0 frees, 10 bytes allocated.
==3900== 
==3900== Use --track-origins=yes to see where uninitialised values come from
==3900== searching for pointers to 1 not-freed blocks.
==3900== checked 180,168 bytes.
==3900== 
==3900== LEAK SUMMARY:
==3900==    definitely lost: 10 bytes in 1 blocks.
==3900==      possibly lost: 0 bytes in 0 blocks.
==3900==    still reachable: 0 bytes in 0 blocks.
==3900==         suppressed: 0 bytes in 0 blocks.
==3900== Rerun with --leak-check=full to see details of leaked memory.
--3900--  memcheck: sanity checks: 1 cheap, 2 expensive
--3900--  memcheck: auxmaps: 0 auxmap entries (0k, 0M) in use
--3900--  memcheck: auxmaps_L1: 0 searches, 0 cmps, ratio 0:10
--3900--  memcheck: auxmaps_L2: 0 searches, 0 nodes
--3900--  memcheck: SMs: n_issued      = 17 (272k, 0M)
--3900--  memcheck: SMs: n_deissued    = 0 (0k, 0M)
--3900--  memcheck: SMs: max_noaccess  = 524287 (8388592k, 8191M)
--3900--  memcheck: SMs: max_undefined = 0 (0k, 0M)
--3900--  memcheck: SMs: max_defined   = 239 (3824k, 3M)
--3900--  memcheck: SMs: max_non_DSM   = 17 (272k, 0M)
--3900--  memcheck: max sec V bit nodes:    0 (0k, 0M)
--3900--  memcheck: set_sec_vbits8 calls: 0 (new: 0, updates: 0)
--3900--  memcheck: max shadow mem size:   4416k, 4M
--3900-- translate:            fast SP updates identified: 1,344 ( 87.2%)
--3900-- translate:   generic_known SP updates identified: 125 (  8.1%)
--3900-- translate: generic_unknown SP updates identified: 71 (  4.6%)
--3900--     tt/tc: 4,047 tt lookups requiring 4,093 probes
--3900--     tt/tc: 4,047 fast-cache updates, 5 flushes
--3900--  transtab: new        1,897 (42,362 -> 661,682; ratio 156:10) [0 scs]
--3900--  transtab: dumped     0 (0 -> ??)
--3900--  transtab: discarded  11 (357 -> ??)
--3900-- scheduler: 199,245 jumps (bb entries).
--3900-- scheduler: 1/2,232 major/minor sched events.
--3900--    sanity: 2 cheap, 2 expensive checks.
--3900--    exectx: 769 lists, 174 contexts (avg 0 per list)
--3900--    exectx: 201 searches, 43 full compares (213 per 1000)
--3900--    exectx: 0 cmp2, 1 cmp4, 0 cmpAll
--3900--  errormgr: 3 supplist searches, 237 comparisons during search
--3900--  errormgr: 3 errlist searches, 3 comparisons during search

```

---

### Post by spjackson on 2010-10-28
I don't get the errors that you get. I am running gcc 4.4.3 on Lucid amd64 with the latest updates, which seems to be the same as your setup. However, my valgrind is a newer version (3.6.0) and is installed from the repositories (whereas yours is in /usr/local/...)

Also, I am using the system default suppression files, no personalised ones.

Here's the short version without -v

```

$ valgrind  ./strlen > valgrind.txt
==3129== Memcheck, a memory error detector
==3129== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==3129== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright info
==3129== Command: ./strlen
==3129==
==3129==
==3129== HEAP SUMMARY:
==3129==     in use at exit: 10 bytes in 1 blocks
==3129==   total heap usage: 1 allocs, 0 frees, 10 bytes allocated
==3129==
==3129== LEAK SUMMARY:
==3129==    definitely lost: 10 bytes in 1 blocks
==3129==    indirectly lost: 0 bytes in 0 blocks
==3129==      possibly lost: 0 bytes in 0 blocks
==3129==    still reachable: 0 bytes in 0 blocks
==3129==         suppressed: 0 bytes in 0 blocks
==3129== Rerun with --leak-check=full to see details of leaked memory
==3129==
==3129== For counts of detected and suppressed errors, rerun with: -v
==3129== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)

```And the longer one:
```

valgrind  ./strlen > valgrind.txt
==3129== Memcheck, a memory error detector
==3129== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==3129== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright                                                                              info
==3129== Command: ./strlen
==3129==
==3129==
==3129== HEAP SUMMARY:
==3129==     in use at exit: 10 bytes in 1 blocks
==3129==   total heap usage: 1 allocs, 0 frees, 10 bytes allocated
==3129==
==3129== LEAK SUMMARY:
==3129==    definitely lost: 10 bytes in 1 blocks
==3129==    indirectly lost: 0 bytes in 0 blocks
==3129==      possibly lost: 0 bytes in 0 blocks
==3129==    still reachable: 0 bytes in 0 blocks
==3129==         suppressed: 0 bytes in 0 blocks
==3129== Rerun with --leak-check=full to see details of leaked memory
==3129==
==3129== For counts of detected and suppressed errors, rerun with: -v
==3129== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)
spj@blackbox:~/tmp$ valgrind -v ./strlen > valgrind.txt
==3151== Memcheck, a memory error detector
==3151== Copyright (C) 2002-2009, and GNU GPL'd, by Julian Seward et al.
==3151== Using Valgrind-3.6.0.SVN-Debian and LibVEX; rerun with -h for copyright                                                                              info
==3151== Command: ./strlen
==3151==
--3151-- Valgrind options:
--3151--    --suppressions=/usr/lib/valgrind/debian-libc6-dbg.supp
--3151--    -v
--3151-- Contents of /proc/version:
--3151--   Linux version 2.6.32-25-generic (buildd@allspice) (gcc version 4.4.3                                                                              (Ubuntu 4.4.3-4ubuntu5) ) #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010
--3151-- Arch and hwcaps: AMD64, amd64-sse3-cx16
--3151-- Page sizes: currently 4096, max supported 4096
--3151-- Valgrind library directory: /usr/lib/valgrind
--3151-- Reading syms from /home/spj/tmp/strlen (0x400000)
--3151-- Reading syms from /lib/ld-2.11.1.so (0x4000000)
--3151-- Reading debug info from /lib/ld-2.11.1.so ..
--3151-- .. CRC mismatch (computed 88039adb wanted c17ec96b)
--3151-- Reading debug info from /usr/lib/debug/lib/ld-2.11.1.so ..
--3151-- Reading syms from /usr/lib/valgrind/memcheck-amd64-linux (0x38000000)
--3151--    object doesn't have a dynamic symbol table
--3151-- Reading suppressions file: /usr/lib/valgrind/debian-libc6-dbg.supp
--3151-- Reading suppressions file: /usr/lib/valgrind/default.supp
--3151-- REDIR: 0x4018290 (strlen) redirected to 0x380402d7 (vgPlain_amd64_linux                                                                             _REDIR_FOR_strlen)
--3151-- Reading syms from /usr/lib/valgrind/vgpreload_core-amd64-linux.so (0x4a                                                                             22000)
--3151-- Reading syms from /usr/lib/valgrind/vgpreload_memcheck-amd64-linux.so (                                                                             0x4c24000)
==3151== WARNING: new redirection conflicts with existing -- ignoring it
--3151--     new: 0x04018290 (strlen              ) R-> 0x04c28710 strlen
--3151-- REDIR: 0x4018100 (index) redirected to 0x4c28320 (index)
--3151-- REDIR: 0x4018180 (strcmp) redirected to 0x4c28cf0 (strcmp)
--3151-- Reading syms from /usr/lib/libstdc++.so.6.0.13 (0x4e2d000)
--3151-- Reading debug info from /usr/lib/libstdc++.so.6.0.13 ..
--3151-- .. CRC mismatch (computed 7b5bd5a5 wanted e2f63673)
--3151--    object doesn't have a symbol table
--3151-- Reading syms from /lib/libm-2.11.1.so (0x5141000)
--3151-- Reading debug info from /lib/libm-2.11.1.so ..
--3151-- .. CRC mismatch (computed 043548c3 wanted a081b93d)
--3151-- Reading debug info from /usr/lib/debug/lib/libm-2.11.1.so ..
--3151-- Reading syms from /lib/libgcc_s.so.1 (0x53c4000)
--3151-- Reading debug info from /lib/libgcc_s.so.1 ..
--3151-- .. CRC mismatch (computed 7c01dfc9 wanted 9d78e511)
--3151--    object doesn't have a symbol table
--3151-- Reading syms from /lib/libc-2.11.1.so (0x55db000)
--3151-- Reading debug info from /lib/libc-2.11.1.so ..
--3151-- .. CRC mismatch (computed 375e41a0 wanted 405b95a9)
--3151-- Reading debug info from /usr/lib/debug/lib/libc-2.11.1.so ..
--3151-- REDIR: 0x565fb00 (__GI_strrchr) redirected to 0x4c28140 (__GI_strrchr)
--3151-- REDIR: 0x4ef8380 (operator new[](unsigned long)) redirected to 0x4c278b                                                                             7 (operator new[](unsigned long))
--3151-- REDIR: 0x5663270 (strchrnul) redirected to 0x4c29a10 (strchrnul)
--3151-- REDIR: 0x565e010 (strlen) redirected to 0x4a225dc (_vgnU_ifunc_wrapper)
==3151== WARNING: new redirection conflicts with existing -- ignoring it
--3151--     new: 0x0565e040 (__GI_strlen         ) R-> 0x04c286b0 strlen
--3151-- REDIR: 0x565e040 (__GI_strlen) redirected to 0x4c286d0 (__GI_strlen)
--3151-- REDIR: 0x5658e10 (free) redirected to 0x4c27036 (free)
==3151==
==3151== HEAP SUMMARY:
==3151==     in use at exit: 10 bytes in 1 blocks
==3151==   total heap usage: 1 allocs, 0 frees, 10 bytes allocated
==3151==
==3151== Searching for pointers to 1 not-freed blocks
==3151== Checked 178,952 bytes
==3151==
==3151== LEAK SUMMARY:
==3151==    definitely lost: 10 bytes in 1 blocks
==3151==    indirectly lost: 0 bytes in 0 blocks
==3151==      possibly lost: 0 bytes in 0 blocks
==3151==    still reachable: 0 bytes in 0 blocks
==3151==         suppressed: 0 bytes in 0 blocks
==3151== Rerun with --leak-check=full to see details of leaked memory
==3151==
==3151== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)
--3151--
--3151-- used_suppression:      2 dl-hack3-cond-1
--3151-- used_suppression:      2 glibc-2.5.x-on-SUSE-10.2-(PPC)-2a
==3151==
==3151== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)

```

---

### Post by blobhunter on 2010-10-29
Many thanks for pointing out the version discrepancy!

I removed the old valgrind version in /usr/local/bin which was masking the newer one installed in /usr/bin. If I remember correctly manually installed valgrind in an older version of Ubuntu (7 or 8?) because it wasn't part of the standard repository.

With the new version, all the problems disappeared.

Again, many thanks, you saved me a lot of grief! It turned out to be a simple mistake on my behalf.

---

