---
title: "Is kernel compilation necessary for compiling kernel modules?"
date: 2008-02-04
forum: Programming Talk
---

### Post by shahzeb.ihsan on 2008-02-04
Hi,

I was trying to compile a kernel module and came across some errors. I'm using Eclipse with CDT to build my code. I just wanted to know if kernel modules can be compiled without recompiling the kernel. If not, how does one go about it, and can it be done with Eclipse?

Maybe a short tutorial/FAQ for programmers starting off with kernel modules and device drivers should be written.

I've already installed "build-essentials" and "linux-headers" and told eclipse to add the include path "/usr/src/linux-headers-2.6.22-14/include", where I've also created a symbolic link "asm" to the "asm-i386" directory. But during compilation I get the following errors:

```

**** Build of configuration Debug for project test_module ****

make -k all 
Building file: ../test_module.c
Invoking: GCC C Compiler
gcc -I/usr/src/linux-headers-2.6.22-14/include -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"test_module.d" -MT"test_module.d" -o"test_module.o" "../test_module.c"
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/bitops.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/alternative.h:9: error: expected specifier-qualifier-list before ‘u8’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/bitops.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/bitops.h:408,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm-generic/bitops/fls64.h: In function ‘fls64’:
/usr/src/linux-headers-2.6.22-14/include/asm-generic/bitops/fls64.h:10: warning: implicit declaration of function ‘fls’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In function ‘hweight_long’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: warning: implicit declaration of function ‘hweight32’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: warning: implicit declaration of function ‘hweight64’
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/system.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:57,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:213: error: expected declaration specifiers or ‘...’ before ‘u8’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:213: error: expected declaration specifiers or ‘...’ before ‘u8’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:214: error: expected declaration specifiers or ‘...’ before ‘u16’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:214: error: expected declaration specifiers or ‘...’ before ‘u16’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:215: error: expected declaration specifiers or ‘...’ before ‘u32’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:215: error: expected declaration specifiers or ‘...’ before ‘u32’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h: In function ‘cmpxchg_386’:
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:222: error: too many arguments to function ‘cmpxchg_386_u8’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:224: error: too many arguments to function ‘cmpxchg_386_u16’
/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:226: error: too many arguments to function ‘cmpxchg_386_u32’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:57,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/system.h: In function ‘sched_cacheflush’:
/usr/src/linux-headers-2.6.22-14/include/asm/system.h:319: warning: implicit declaration of function ‘wbinvd’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:290: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: In function ‘double_spin_lock’:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: error: ‘l1_first’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: error: for each function it appears in.)
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:309: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: In function ‘double_spin_unlock’:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:313: error: ‘l1_taken_first’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:86,
                 from /usr/src/linux-headers-2.6.22-14/include/asm/processor.h:22,
                 from /usr/src/linux-headers-2.6.22-14/include/asm/atomic.h:5,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_zero’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:134: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:137: warning: implicit declaration of function ‘BITS_TO_LONGS’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:138: warning: implicit declaration of function ‘memset’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:138: warning: incompatible implicit declaration of built-in function ‘memset’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_fill’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:147: warning: incompatible implicit declaration of built-in function ‘memset’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:149: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_copy’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:155: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:159: warning: implicit declaration of function ‘memcpy’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:159: warning: incompatible implicit declaration of built-in function ‘memcpy’
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_and’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:166: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_or’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:175: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_xor’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:184: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_andnot’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:193: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_complement’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:202: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_equal’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:211: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:215: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_intersects’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:220: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:224: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_subset’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:229: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:233: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_empty’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:237: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:241: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_full’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:245: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:249: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_weight’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:253: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_shift_right’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:261: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h: In function ‘bitmap_shift_left’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitmap.h:270: error: ‘BITS_PER_LONG’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/processor.h:22,
                 from /usr/src/linux-headers-2.6.22-14/include/asm/atomic.h:5,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:88: error: expected specifier-qualifier-list before ‘DECLARE_BITMAP’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpu_set’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:94: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpu_clear’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:100: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_setall’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:106: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_clear’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:112: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpu_test_and_set’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:121: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_and’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:128: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:128: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:128: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_or’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_xor’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:142: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:142: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:142: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_andnot’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:150: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:150: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:150: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_complement’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:157: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:157: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_equal’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:164: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:164: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_intersects’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:171: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:171: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_subset’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:178: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:178: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_empty’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:184: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_full’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:190: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_weight’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:196: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_shift_right’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:204: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:204: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_shift_left’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:212: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:212: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpumask_scnprintf’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:273: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpumask_parse_user’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:281: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpulist_scnprintf’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:289: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpulist_parse’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:295: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpu_remap’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:303: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:303: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h: In function ‘__cpus_remap’:
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.22-14/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/atomic.h:5,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:83: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: In function ‘set_in_cr4’:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:157: warning: implicit declaration of function ‘read_cr4’
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:159: warning: implicit declaration of function ‘write_cr4’
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:427: warning: ‘struct pt_regs’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:427: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: In function ‘native_load_esp0’:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:506: warning: implicit declaration of function ‘unlikely’
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:508: warning: implicit declaration of function ‘wrmsr’
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: In function ‘native_get_debugreg’:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:531: warning: implicit declaration of function ‘BUG’
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.22-14/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/atomic.h: In function ‘atomic_add_unless’:
/usr/src/linux-headers-2.6.22-14/include/asm/atomic.h:237: warning: implicit declaration of function ‘likely’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/list.h:970:2: warning: #warning "don't include kernel headers in userspace"
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:19,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h:72: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h:78: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h: In function ‘percpu_free’:
/usr/src/linux-headers-2.6.22-14/include/linux/percpu.h:91: warning: implicit declaration of function ‘kfree’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:21,
                 from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/asm/module.h:64:2: error: #error unknown processor family
In file included from ../test_module.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/module.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:48: error: field ‘attr’ has incomplete type
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:59: error: field ‘kobj’ has incomplete type
../test_module.c:13: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__attribute_used__’
../test_module.c:14: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__attribute_used__’
make: *** [test_module.o] Error 1
make: Target `all' not remade because of errors.
Build complete for project test_module

```

Any hep would be greatly appreciated.

Regards,
Shahzeb

---

### Post by shahzeb.ihsan on 2008-02-04
So, I've finally figured out how to compile a module using the following make file:

```

obj-m  := test_module.o

KDIR   := /usr/src/linux-headers-2.6.22-14-generic
PWD    := $(shell pwd)

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```

I also executed the following command in /usr/src/linux-headers-2.6.22-14-generic:

```

make menuconfig

```

But exited once the configuration dialog opened because I read somewhere that the "HOSTCC scripts/" step was necessary (happen before the dialog pops up).

So, are the steps that I followed OK? I mean, I know it worked - but is this the correct way?

---

### Post by JamesUser on 2008-02-04
You don't need to run make menuconfig under /usr/src/linux-headers-2.6.22-14-generic unless you want to change your kernel configuration and recompile the kernel, I suppose.

Other than that, I think you have done it the right way.

You might want to read this.. [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

Here's an intro
[http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html?page=1)

and here's another.. [http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0)

---

### Post by shahzeb.ihsan on 2008-02-04
That is the book I am using. I was compiling the "Hello World" module given in the second chapter :)

OK, so now for my second question, can all this be done using Eclipse?

---

### Post by JamesUser on 2008-02-04
Great start... I never went beyond the third chapter in that book.

No idea. I only used vi. You can try and tell me as well if eclipse would work for that.

---

