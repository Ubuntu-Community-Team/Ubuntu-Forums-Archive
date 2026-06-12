---
title: "How to address section mismatch error properly"
date: 2014-12-31
forum: Programming Talk
---

### Post by shahin on 2014-12-31
I am doing some cross compiling; Linux -> armeabi-android platform, and get a section mismatch error as follows: 
```
ERROR: modpost: Found 2 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
To build the kernel despite the mismatches, build with:
'make CONFIG_NO_ERROR_ON_MISMATCH=y'
(NOTE: This is not recommended)
/home/sansari/android/kernel/scripts/Makefile.modpost:98: recipe for target 'vmlinux.o' failed
make[1]: *** [vmlinux.o] Error 1
Makefile:935: recipe for target 'vmlinux.o' failed
make: *** [vmlinux.o] Error
```

I found a really good link that explain why I get it, and how to fix valid instance of it. But I think I need a little more help on how to determine what is a valid instance. [http://stackoverflow.com/questions/6807766/linux-kernel-config-debug-section-mismatch-make-errors]("here") is the link. 

Here is the output of make when I ran it a 2nd time with the debug option: 

```
WARNING: vmlinux.o(.data+0x8434): Section mismatch in reference from the variable msm_mpm_debug_mask to the function 

.init.text:mpm_irq_domain_linear_size()
The variable msm_mpm_debug_mask references
the function __init mpm_irq_domain_linear_size()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

WARNING: vmlinux.o(.data+0x844c): Section mismatch in reference from the variable msm_mpm_debug_mask to the function 

.init.text:mpm_irq_domain_legacy_size()
The variable msm_mpm_debug_mask references
the function __init mpm_irq_domain_legacy_size()
If the reference is valid then annotate the
variable with __init* or __refdata (see linux/init.h) or name the variable:
*_template, *_timer, *_sht, *_ops, *_probe, *_probe_one, *_console

To build the kernel despite the mismatches, build with:
'make CONFIG_NO_ERROR_ON_MISMATCH=y'
(NOTE: This is not recommended)
/home/sansari/android/kernel/scripts/Makefile.modpost:98: recipe for target 'vmlinux.o' failed
make[1]: *** [vmlinux.o] Error 1e 
Makefile:935: recipe for target 'vmlinux.o' failed
make: *** [vmlinux.o] Error 2

```

The other part of my question is once I find out the call is valid, then I need to change _init to something else? is that it? What is the call is not valid? What should do then? Should I remove this call from a file? Which file is that please? BTW, I have read the Linux boot process and can appreciate why make is giving this error. It is also so interesting to me that Android is based on Linux and I can leverage my minimal understanding of boot process here.

---

### Post by schragge on 2014-12-31
Please, have a look at [this](http://forum.xda-developers.com/google-nexus-5/help/solved-stock-kernel-build-problems-t2532147). The recommendation there is just to use another toolchain.

---

