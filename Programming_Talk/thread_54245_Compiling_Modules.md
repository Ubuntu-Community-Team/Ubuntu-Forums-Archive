---
title: "Compiling Modules"
date: 2005-08-04
forum: Programming Talk
---

### Post by adwait on 2005-08-04
Hello,

I am just getting started into module programming, and am trying to compile my hello world program....but gcc gives me a whole bunch of errors, related to the included files. eg:
```

/usr/include/linux/bitmap.h: In function `void bitmap_copy(long unsigned int*,
   const long unsigned int*, int)':
/usr/include/linux/bitmap.h:78: error: `BITS_TO_LONGS' undeclared (first use
   this function)
/usr/include/linux/bitmap.h:78: error: `memcpy' undeclared (first use this
   function)
/usr/include/linux/bitmap.h: In function `void bitmap_shift_right(long unsigned
   int*, const long unsigned int*, int, int)':
/usr/include/linux/bitmap.h:85: error: `__shr_tmp' undeclared (first use this
   function)
/usr/include/linux/bitmap.h:85: error: `DECLARE_BITMAP' undeclared (first use
   this function)
/usr/include/linux/bitmap.h: In function `void bitmap_shift_left(long unsigned
   int*, const long unsigned int*, int, int)':
/usr/include/linux/bitmap.h:98: error: `__shl_tmp' undeclared (first use this
   function)
/usr/include/linux/bitmap.h:98: error: `DECLARE_BITMAP' undeclared (first use
   this function)
/usr/include/linux/bitmap.h: In function `void bitmap_and(long unsigned int*,
   const long unsigned int*, const long unsigned int*, int)':
/usr/include/linux/bitmap.h:111: error: `BITS_TO_LONGS' undeclared (first use
   this function)
/usr/include/linux/bitmap.h: In function `void bitmap_or(long unsigned int*,
   const long unsigned int*, const long unsigned int*, int)':
/usr/include/linux/bitmap.h:121: error: `BITS_TO_LONGS' undeclared (first use
   this function)
/usr/include/linux/bitmap.h: In function `int bitmap_weight(const long unsigned
   int*, int)':
/usr/include/linux/bitmap.h:147: error: `hweight64' undeclared (first use this
   function)
In file included from /usr/include/linux/sched.h:15,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/linux/cpumask.h: At global scope:
/usr/include/linux/cpumask.h:15: error: `BITS_TO_LONGS' was not declared in
   this scope
In file included from /usr/include/linux/sched.h:15,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/linux/cpumask.h: In function `int next_online_cpu(int, cpumask)':
/usr/include/linux/cpumask.h:56: error: 'struct cpumask_t' has no member named
   'val'
/usr/include/linux/cpumask.h:57: error: 'struct cpumask_t' has no member named
   'mask'
/usr/include/linux/cpumask.h:57: error: 'struct cpumask_t' has no member named
   'mask'
In file included from /usr/include/linux/sched.h:21,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/asm/mmu.h: At global scope:
/usr/include/asm/mmu.h:13: error: field `sem' has incomplete type
In file included from /usr/include/asm/smp.h:16,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/asm/fixmap.h:72: error: `FIX_ACPI_PAGES' was not declared in this
   scope
/usr/include/asm/fixmap.h:72: error: enumerator value for `FIX_ACPI_END' not
   integer constant
/usr/include/asm/fixmap.h:84: error: type specifier omitted for parameter `
   pgprot_t'
/usr/include/asm/fixmap.h:84: error: parse error before `)' token
/usr/include/asm/fixmap.h: In function `long unsigned int virt_to_fix(long
   unsigned int)':
/usr/include/asm/fixmap.h:144: error: `BUG_ON' undeclared (first use this
   function)
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
.....
/usr/include/linux/smp.h:65: error: `barrier' undeclared (first use this
   function)
/usr/include/linux/smp.h:68: error: `TIF_NEED_RESCHED' undeclared (first use
   this function)
/usr/include/linux/smp.h:68: error: `test_thread_flag' undeclared (first use
   this function)
/usr/include/linux/smp.h:68: error: `unlikely' undeclared (first use this
   function)
In file included from /usr/include/linux/signal.h:6,
                 from /usr/include/linux/sched.h:25,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/asm/signal.h: At global scope:
/usr/include/asm/signal.h:29: error: conflicting types for `typedef long
   unsigned int sigset_t'
/usr/include/sys/select.h:38: error: previous declaration as `typedef struct
   __sigset_t sigset_t'
In file included from /usr/include/linux/sched.h:29,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/linux/completion.h:15: error: 'wait_queue_head_t' is used as a
   type, but is not defined as a type.
/usr/include/linux/completion.h: In function `void init_completion(completion*)
   ':
/usr/include/linux/completion.h:27: error: 'struct completion' has no member
   named 'wait'
/usr/include/linux/completion.h:27: error: `init_waitqueue_head' undeclared
   (first use this function)
In file included from /usr/include/linux/sched.h:30,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/linux/pid.h: At global scope:
/usr/include/linux/pid.h:18: error: field `task_list' has incomplete type
/usr/include/linux/pid.h:19: error: field `hash_chain' has incomplete type
/usr/include/linux/pid.h:24: error: field `pid_chain' has incomplete type
In file included from /usr/include/linux/sched.h:102,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/linux/timer.h:11: error: field `entry' has incomplete type
/usr/include/linux/timer.h: In function `void init_timer(timer_list*)':
/usr/include/linux/timer.h:45: error: `spin_lock_init' undeclared (first use
   this function)
In file included from /usr/include/linux/sched.h:104,
                 from /usr/include/linux/module.h:10,
                 from mod.cpp:1:
/usr/include/asm/processor.h: In function `void load_esp0(tss_struct*, long
   unsigned int)':
/usr/include/asm/processor.h:454: error: `unlikely' undeclared (first use this
   function)
In file included from mod.cpp:1:
/usr/include/linux/module.h: At global scope:
/usr/include/linux/module.h:190: error: field `list' has incomplete type
mod.cpp: In function `int init_module()':
mod.cpp:6: error: `KERN_INFO' undeclared (first use this function)
mod.cpp:6: error: parse error before string constant
mod.cpp: In function `void cleanup_module()':
mod.cpp:13: error: parse error before string constant

```

This is just a small portion of the errors.....there are many more similar ones. Any idea why??

---

