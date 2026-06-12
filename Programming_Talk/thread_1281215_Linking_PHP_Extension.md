---
title: "Linking PHP Extension"
date: 2009-10-03
forum: Programming Talk
---

### Post by bfrosty on 2009-10-03
Hi,

I'm writing a PHP extension in C to talk to Matlab, but I'm finding that when I run it, the PHP script dies and I find this in the Apache log:

"/usr/sbin/apache2: symbol lookup error: /usr/lib/php5/20060613+lfs/phpmat.so: undefined symbol: engOpen"

I created a test program and ran it, and everything went okay, but I find that when I haven't got LD_LIBRARY_PATH set, I get a similar error:

"./phpmat: error while loading shared libraries: libmat.so: cannot open shared object file: No such file or directory"

How do I link the PHP extension to the matlab library in /usr/local/matlabR2009a/bin/glnx86/libeng.so ?

Much appreciated

```

ldd phpmat.so
        linux-gate.so.1 =>  (0xb8081000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7f10000)
        /lib/ld-linux.so.2 (0xb8082000)

```

```

nm phpmat.so
00001f14 a _DYNAMIC
00001ff4 a _GLOBAL_OFFSET_TABLE_
         w _Jv_RegisterClasses
00001f04 d __CTOR_END__
00001f00 d __CTOR_LIST__
00001f0c d __DTOR_END__
00001f08 d __DTOR_LIST__
00000a44 r __FRAME_END__
00001f10 d __JCR_END__
00001f10 d __JCR_LIST__
000020e8 A __bss_start
         U __ctype_b_loc@@GLIBC_2.3
         w __cxa_finalize@@GLIBC_2.1.3
000009d0 t __do_global_ctors_aux
000006d0 t __do_global_dtors_aux
00002040 d __dso_handle
         w __gmon_start__
00000787 t __i686.get_pc_thunk.bx
0000099e t __i686.get_pc_thunk.cx
         U __stack_chk_fail@@GLIBC_2.4
000009b0 t __stack_chk_fail_local
000020e8 A _edata
000020f0 A _end
         U _estrdup
00000a08 T _fini
000005b8 T _init
000020e8 b completed.6635
000020ec b dtor_idx.6637
         U engClose
         U engEvalString
         U engOpen
         U engOutputBuffer
00000750 t frame_dummy
00000820 T getEngResult
00000790 T get_module
000020c0 d phpmat_functions
00002060 D phpmat_module_entry
         U strlen@@GLIBC_2.0
000007b0 T trimwhitespace
         U zend_parse_parameters
00000910 T zif_getEngResult

```

---

### Post by mdesign on 2010-04-01
Hi!

I have exactly the same problem. Im tried with PHP_ADD_LIBRARY_WITH_PATH, but not helped...

Can anyone help me?

---

