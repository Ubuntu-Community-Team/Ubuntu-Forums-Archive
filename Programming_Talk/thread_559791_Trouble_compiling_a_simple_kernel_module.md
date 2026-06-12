---
title: "Trouble compiling a simple kernel module"
date: 2007-09-25
forum: Programming Talk
---

### Post by edfredcoder on 2007-09-25
Hello,
I am trying to write and compile a kernel module. It is very simple. Here is the source code:

hello.c:
```


#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("GPL");


static int __init hello_init()
{
        return 0;
}

static void __exit hello_exit()
{
}

module_init(hello_init);
module_exit(hello_exit); 

```

I am compiling with:
```

gcc -I /lib/modules/2.6.21-2-686/build/include/ -c hello.c 

```

I get a lot of errors:
```

In file included from /lib/modules/2.6.21-2-686/build/include/linux/bitops.h:9,
                 from /lib/modules/2.6.21-2-686/build/include/linux/thread_info.h:20,
                 from /lib/modules/2.6.21-2-686/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/asm/bitops.h:244: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int'
In file included from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:57,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/system.h: In function 'cmpxchg_386':
/lib/modules/2.6.21-2-686/build/include/asm/system.h:355: error: too many arguments to function 'cmpxchg_386_u8'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:357: error: too many arguments to function 'cmpxchg_386_u16'
/lib/modules/2.6.21-2-686/build/include/asm/system.h:359: error: too many arguments to function 'cmpxchg_386_u32'
In file included from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h: At top level:
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:290: error: expected declaration specifiers or '...' before 'bool'
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h: In function 'double_spin_lock':
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:294: error: 'l1_first' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:294: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:294: error: for each function it appears in.)
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h: At top level:
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:309: error: expected declaration specifiers or '...' before 'bool'
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h: In function 'double_spin_unlock':
/lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:313: error: 'l1_taken_first' undeclared (first use in this function)
In file included from /lib/modules/2.6.21-2-686/build/include/asm/processor.h:17,
                 from /lib/modules/2.6.21-2-686/build/include/asm/atomic.h:5,
                 from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:326,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/asm/msr.h: At top level:
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:90: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:90: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:90: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h: In function 'rdmsr_on_cpu':
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:92: error: 'l' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:92: error: 'h' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:92: error: 'msr_no' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:92: error: invalid lvalue in asm output 0
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:92: error: invalid lvalue in asm output 1
/lib/modules/2.6.21-2-686/build/include/asm/msr.h: At top level:
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:94: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:94: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:94: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.21-2-686/build/include/asm/msr.h: In function 'wrmsr_on_cpu':
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:96: error: 'msr_no' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:96: error: 'l' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/asm/msr.h:96: error: 'h' undeclared (first use in this function)
In file included from /lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:86,
                 from /lib/modules/2.6.21-2-686/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.21-2-686/build/include/asm/atomic.h:5,
                 from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:326,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_zero':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:134: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:138: warning: incompatible implicit declaration of built-in function 'memset'
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_fill':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:147: warning: incompatible implicit declaration of built-in function 'memset'
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:149: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_copy':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:155: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:159: warning: incompatible implicit declaration of built-in function 'memcpy'
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_and':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:166: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_or':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:175: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_xor':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:184: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_andnot':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:193: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_complement':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:202: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_equal':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:211: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_intersects':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:220: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_subset':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:229: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_empty':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:237: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_full':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:245: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_weight':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:253: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_shift_right':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:261: error: 'BITS_PER_LONG' undeclared (first use in this function)
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h: In function 'bitmap_shift_left':
/lib/modules/2.6.21-2-686/build/include/linux/bitmap.h:270: error: 'BITS_PER_LONG' undeclared (first use in this function)
In file included from /lib/modules/2.6.21-2-686/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.21-2-686/build/include/asm/atomic.h:5,
                 from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:326,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: At top level:
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:88: error: expected specifier-qualifier-list before 'DECLARE_BITMAP'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpu_set':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:94: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpu_clear':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:100: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_setall':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:106: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_clear':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:112: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpu_test_and_set':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:121: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_and':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:128: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:128: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:128: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_or':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:135: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:135: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:135: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_xor':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:142: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:142: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:142: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_andnot':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:150: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:150: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:150: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_complement':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:157: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:157: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_equal':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:164: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:164: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_intersects':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:171: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:171: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_subset':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:178: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:178: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_empty':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:184: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_full':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:190: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_weight':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:196: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_shift_right':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:204: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:204: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_shift_left':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:212: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:212: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpumask_scnprintf':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:273: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpumask_parse_user':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:281: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpulist_scnprintf':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:289: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpulist_parse':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:295: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpu_remap':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:303: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:303: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h: In function '__cpus_remap':
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:311: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:311: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:311: error: 'cpumask_t' has no member named 'bits'
/lib/modules/2.6.21-2-686/build/include/linux/cpumask.h:311: error: 'cpumask_t' has no member named 'bits'
In file included from /lib/modules/2.6.21-2-686/build/include/asm/atomic.h:5,
                 from /lib/modules/2.6.21-2-686/build/include/linux/spinlock.h:326,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/asm/processor.h: At top level:
/lib/modules/2.6.21-2-686/build/include/asm/processor.h:82: error: 'CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
/lib/modules/2.6.21-2-686/build/include/asm/processor.h:82: error: requested alignment is not a constant
/lib/modules/2.6.21-2-686/build/include/asm/processor.h:472: warning: 'struct pt_regs' declared inside parameter list
/lib/modules/2.6.21-2-686/build/include/asm/processor.h:472: warning: its scope is only this definition or declaration, which is pro                                       bably not what you want
In file included from /lib/modules/2.6.21-2-686/build/include/linux/module.h:10,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/list.h:959:2: warning: #warning "don't include kernel headers in userspace"
In file included from /lib/modules/2.6.21-2-686/build/include/asm/local.h:4,
                 from /lib/modules/2.6.21-2-686/build/include/linux/module.h:19,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/percpu.h:65: error: expected declaration specifiers or '...' before 'gfp_t'
/lib/modules/2.6.21-2-686/build/include/linux/percpu.h:71: error: expected declaration specifiers or '...' before 'gfp_t'
/lib/modules/2.6.21-2-686/build/include/linux/percpu.h:77: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'void'
In file included from /lib/modules/2.6.21-2-686/build/include/linux/module.h:21,
                 from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/asm/module.h:62:2: error: #error unknown processor family
In file included from hello.c:2:
/lib/modules/2.6.21-2-686/build/include/linux/module.h:48: error: field 'attr' has incomplete type
/lib/modules/2.6.21-2-686/build/include/linux/module.h:59: error: field 'kobj' has incomplete type
hello.c:12: error: variable or field '__attribute_used__' declared void
hello.c:12: error: expected ',' or ';' before 'hello_exit'
hello.c:16: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__attribute_used__'
hello.c:17: error: expected '=', ',', ';', 'asm' or '__attribute__' before '__attribute_used__' 

```

I also installed the kernel headers:
```

sudo apt-get install linux-headers-2.6-686

```
which I assume I need, but those didn't help.

Yikes! I must be doing something wrong. Can anyone help me with this? 

-Kevin

---

### Post by geraldm on 2007-09-25
This script compiles here --  ALL ON ONE LINE -- gcc:

#!/bin/bash
gcc -I /lib/modules/2.6.21.1n/build/include -D__KERNEL__ -DMODULE -DCONFIG_MK7 -DCONFIG_HZ=250 -DCONFIG_X86_L1_CACHE_SHIFT=6 -c hello.c

Pass the architecture on the command line.  Mine was CONFIG_MK7 (use yours)

I dug some information out of my top source .config file

% grep 'HZ' $LIN/.config
# CONFIG_NO_HZ is not set
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=250

When another error appeared, I also used its .config file value

% grep "_X86_L1" $LIN/.config
CONFIG_X86_L1_CACHE_SHIFT=6

You possibly may not need to use the parameters that are shown
above, but you may have to find the proper values from your
top source .config file.  This file can sometimes be found in 
your boot directory as "config" or whatever config file is used
to build your kernel.

Gerald

---

