---
title: "A bunch of errors without even modifying"
date: 2010-10-15
forum: Packaging and Compiling Programs
---

### Post by montraydavis on 2010-10-15
Hello, I am currently building a kernel from scratch based off of the linux kernel.
I have the kernel up and running, but, when trying to compile a module for the kernel, 
I get a bunch of crazy errors.!

I downloaded the linux-2.6.35.7 ( as well as a few others which didn't work either ) from [http://kernel.org/](http://kernel.org/)
No luck at all. It throws me a bunch of crazy errors. The errors aren't coming from my program source. The errors
seem to be coming from the actual module header that I downloaded.... This happens with all of the kernels I download.

Anyone have a clue why this might be?

psilowin.c source code:

```

#include <linux/kernel.h> //This works fine
#include <linux/module.h> //Whenever I insert this, I get the errors posted below :\

int init_module(void)
{
  printk("module initiated");
}

int cleanup_module(void)
{

}

```

You see, I don't see how I could be getting any error :\

```

                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/smp.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/smp.h:20: error: expected specifier-qualifier-list before ‘u16’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/topology.h:34,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:7,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:22,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/percpu.h:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_kernel_percpu_address’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/percpu.h:154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘setup_per_cpu_areas’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/percpu.h:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘per_cpu_ptr_to_phys’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:22,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:121: error: expected ‘)’ before ‘gfp_flags’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:22,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:185:2: error: #error ZONES_SHIFT too large to create GFP_ZONE_TABLE integer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:216: error: expected ‘)’ before ‘flags’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:241: error: expected ‘)’ before ‘flags’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:258: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: In function ‘node_zonelist’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:260: warning: implicit declaration of function ‘gfp_zonelist’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:260: error: ‘flags’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:271: error: expected ‘)’ before ‘gfp_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:275: error: expected ‘)’ before ‘gfp_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:281: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: In function ‘alloc_pages_node’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:288: warning: implicit declaration of function ‘__alloc_pages’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:288: error: ‘gfp_mask’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:288: error: too many arguments to function ‘node_zonelist’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:288: warning: return makes pointer from integer without a cast
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:291: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: In function ‘alloc_pages_exact_node’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:296: error: ‘gfp_mask’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:296: error: too many arguments to function ‘node_zonelist’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:296: warning: return makes pointer from integer without a cast
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:316: error: expected ‘)’ before ‘gfp_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:317: error: expected ‘)’ before ‘gfp_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:319: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:340: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gfp_allowed_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:342: error: expected ‘)’ before ‘mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/gfp.h:343: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘clear_gfp_allowed_mask’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/math64.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:4,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:25,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/timer.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:8,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/asm/div64.h:54:3: error: #error do_div() does not yet support the C64
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:4,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:25,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/timer.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:8,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/math64.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘div_u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/math64.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘div_s64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/math64.h:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iter_div_u64_rem’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/math64.h:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__iter_div_u64_rem’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:25,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/timer.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:8,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:81: warning: type defaults to ‘int’ in declaration of ‘u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:81: error: expected ‘,’ or ‘;’ before ‘jiffies_64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_jiffies_64’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:25,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/timer.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:8,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:257:31: error: division by zero in #if
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jiffies_to_clock_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:308: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jiffies_64_to_clock_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:309: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘nsec_to_clock_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/jiffies.h:310: error: expected ‘)’ before ‘n’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/timer.h:5,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:8,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:47: error: expected specifier-qualifier-list before ‘s64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_set’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:153: error: unknown field ‘tv’ specified in initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:153: error: extra brace group at end of initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:153: error: (near initialization for ‘(anonymous)’)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:153: warning: excess elements in union initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:153: warning: (near initialization for ‘(anonymous)’)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_sub’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:167: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:167: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:167: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:168: error: ‘ktime_t’ has no member named ‘tv’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:169: error: ‘ktime_t’ has no member named ‘tv’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:169: error: ‘NSEC_PER_SEC’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_add’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:185: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:185: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:185: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:194: error: ‘ktime_t’ has no member named ‘tv’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:194: error: ‘NSEC_PER_SEC’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:195: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:195: error: ‘u32’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:207: error: expected declaration specifiers or ‘...’ before ‘u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:216: error: expected declaration specifiers or ‘...’ before ‘u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘timespec_to_ktime’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:226: error: unknown field ‘tv’ specified in initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:226: error: extra brace group at end of initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:226: error: (near initialization for ‘(anonymous)’)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:226: error: ‘s32’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:226: error: expected ‘}’ before ‘ts’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘timeval_to_ktime’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:238: error: unknown field ‘tv’ specified in initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:238: error: extra brace group at end of initializer
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:238: error: (near initialization for ‘(anonymous)’)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:238: error: ‘s32’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:238: error: expected ‘}’ before ‘tv’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_to_timespec’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:250: error: ‘time_t’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:250: error: expected ‘}’ before ‘kt’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_to_timeval’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:263: error: ‘time_t’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:263: error: expected ‘}’ before ‘kt’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:273: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ktime_to_ns’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: In function ‘ktime_equal’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:289: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:289: error: ‘ktime_t’ has no member named ‘tv64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:290: warning: control reaches end of non-void function
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:292: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ktime_to_us’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:298: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ktime_to_ms’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:304: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ktime_us_delta’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:309: warning: type defaults to ‘int’ in declaration of ‘u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:309: error: expected ‘;’, ‘,’ or ‘)’ before ‘usec’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:314: warning: type defaults to ‘int’ in declaration of ‘u64’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:314: error: expected ‘;’, ‘,’ or ‘)’ before ‘usec’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/ktime.h:336: error: expected ‘)’ before ‘ns’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:26,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:26: error: expected specifier-qualifier-list before ‘atomic_long_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h: In function ‘to_delayed_work’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:48: warning: implicit declaration of function ‘container_of’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:48: error: expected expression before ‘struct’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:48: warning: return makes pointer from integer without a cast
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:256: error: ‘struct work_struct’ has no member named ‘data’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h: In function ‘__cancel_delayed_work’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/workqueue.h:271: error: ‘struct work_struct’ has no member named ‘data’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:13,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:71: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h: In function ‘call_usermodehelper_fns’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:93: error: ‘gfp_t’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:93: error: expected ‘;’ before ‘gfp_mask’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:95: error: ‘gfp_mask’ undeclared (first use in this function)
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kmod.h:95: error: too many arguments to function ‘call_usermodehelper_setup’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:21,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:16,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:33: error: expected specifier-qualifier-list before ‘mode_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:63: error: expected specifier-qualifier-list before ‘mode_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:97: error: expected specifier-qualifier-list before ‘ssize_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:118: error: expected specifier-qualifier-list before ‘ssize_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:228: error: expected declaration specifiers or ‘...’ before ‘mode_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/sysfs.h:336: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysfs_init’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:24,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:16,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kref.h:21: error: expected specifier-qualifier-list before ‘atomic_t’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:16,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uevent_seqnum’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:77: error: expected declaration specifiers or ‘...’ before ‘va_list’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_add’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_init_and_add’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create_and_add’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_rename’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_move’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:105: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:131: error: expected specifier-qualifier-list before ‘ssize_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:200: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_register’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_create_and_add’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h: In function ‘to_kset’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:208: error: expected expression before ‘struct’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/kobject.h:208: warning: pointer/integer type mismatch in conditional expression
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:17,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/moduleparam.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/moduleparam.h:44: error: expected specifier-qualifier-list before ‘u16’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:42,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/tracepoint.h:19,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:18,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h:27: error: expected specifier-qualifier-list before ‘wait_queue_head_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h: In function ‘init_completion’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h:76: warning: implicit declaration of function ‘init_waitqueue_head’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h:76: error: ‘struct completion’ has no member named ‘wait’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘try_wait_for_completion’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/completion.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_done’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/tracepoint.h:19,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:18,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:73:2: error: #error "Unknown RCU implementation specified to kernel configuration"
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/tracepoint.h:19,
                 from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:18,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h: In function ‘rcu_read_lock’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:312: warning: implicit declaration of function ‘__rcu_read_lock’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h: In function ‘rcu_read_unlock’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:336: warning: implicit declaration of function ‘__rcu_read_unlock’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h: In function ‘rcu_read_lock_bh’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:352: warning: implicit declaration of function ‘__rcu_read_lock_bh’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h: In function ‘rcu_read_unlock_bh’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:366: warning: implicit declaration of function ‘__rcu_read_unlock_bh’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:386: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/rcupdate.h:405: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’
In file included from /home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:18,
                 from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/tracepoint.h: In function ‘tracepoint_synchronize_unregister’:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/tracepoint.h:80: warning: implicit declaration of function ‘synchronize_sched’
In file included from bin/modules/psilowin.c:1:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h: At top level:
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:53: error: expected specifier-qualifier-list before ‘ssize_t’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:572: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_address’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:577: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_percpu_address’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:582: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_text_address’
bin/modules/psilowin.c:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘div_u64’
bin/modules/psilowin.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_percpu_address’
bin/modules/psilowin.c: In function ‘init_module’:
bin/modules/psilowin.c:10: warning: control reaches end of non-void function
bin/modules/psilowin.c: At top level:
bin/modules/psilowin.c:12: error: conflicting types for ‘cleanup_module’
/home/plumos/Desktop/linux-2.6.35.7/include/linux/module.h:71: error: previous declaration of ‘cleanup_module’ was here
bin/modules/psilowin.c: In function ‘cleanup_module’:
bin/modules/psilowin.c:15: warning: control reaches end of non-void function
make: *** [all] Error 1

```

---

### Post by montraydavis on 2010-10-15
Ok. With a bit of Makefile configuration (and google searching), I fixed it. Thanks anyways.. But now there is just one more issue.

This is the structure of the Operating System I am working on.

Bootloader -> Kernel -> OS-HELPER
                                      OS

The OS-HELPER will be ran on top of the Operating System, and will manage small functions [ie. application resources, networking, etc...]

The OS will be... Well.... The OS ! (:
It will handle the core functions, mainly for *a developing experience*.

Kernel is the kernel blah.

Anyhow, I am wondering how to link a "module" into the kernel?
[Kernel and Bootloader] are already up and running.

```

undefined reference to `printk'

```It's these darn 'refrences' that keep me from getting more into the development.
Linux-Headers were a pain to get prepared. Seems all of my errors come from the make
process. I use a simple process

```

ld -T bin/link.ld -o $(output)/kernel.bin $(output)/bootloader.o $(output)/kernel.o $(output)/screen.o $(modules)/psilowin.o 

```That packs in the bootloader, the kernel, screen functions ( such as writing ), and psilowin (the OS-HELPER I mentioned earlier)

Anywho, that right there is what gives me the 'undefined reference to printk'.
I'm not an expert on Linux Kernel, I've only been using it for a few years, but, I know enough to get started. Seems like I am missing a library, and I can't seem to include it in the linking process!

Any suggestions?

PS: When I say a module, I mean any linux module ( ie: if I were to get a set of specific modules for the kernel to load )

---

