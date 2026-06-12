---
title: "help -- compiler problem with driver source"
date: 2010-01-27
forum: Packaging and Compiling Programs
---

### Post by chh0605 on 2010-01-27
Dear Helper:
   I met a compiler problem with driver source as below:

1. uname -r is 2.6.31-17-generic and put kernel source linux-2.6.31 into /usr/src/
2. make a link with linux/linux-2.6.31/include/linux/
3. compiler simple code with usb driver using Anjuta
4. get a lot of compiler error log for the source driver as below:

How do I compiler and get pass?

make
make  all-recursive
make[1]: Entering directory `/home/test/test_project/test-001/Debug'
make[1]: Entering directory `/home/test/test_project/test-001/Debug'
Making all in src
make[2]: Entering directory `/home/test/test_project/test-001/Debug/src'
make[2]: Entering directory `/home/test/test_project/test-001/Debug/src'
cd /home/test/test_project/test-001 && /bin/sh /home/test/test_project/test-001/missing --run automake-1.11 --gnu src/Makefile
/home/test/test_project/test-001/Debug/src/src/Makefile.am:16: compiling `main.c' with per-target flags requires `AM_PROG_CC_C_O' in `configure.ac'
cd .. && /bin/sh ./config.status src/Makefile depfiles
config.status: creating src/Makefile
config.status: executing depfiles commands
make[2]: Leaving directory `/home/test/test_project/test-001/Debug/src'
make[2]: Leaving directory `/home/test/test_project/test-001/Debug/src'
make[2]: Entering directory `/home/test/test_project/test-001/Debug/src'
make[2]: Entering directory `/home/test/test_project/test-001/Debug/src'
CC     test_001-shuttle_usbat.o
gcc: CONCURRENCY_LEVEL=2: No such file or directory
gcc: NOEXTRAS=1: No such file or directory
gcc: skipabi=true: No such file or directory
gcc: skipmodule=true: No such file or directory
gcc: fakeroot: No such file or directory
gcc: debian/rules: No such file or directory
gcc: binary-core2: No such file or directory
In file included from /usr/src/asm/percpu.h:45,
from /usr/src/asm/current.h:5,
from /usr/src/asm/processor.h:15,
from /usr/src/linux/prefetch.h:14,
from /usr/src/linux/list.h:6,
from /usr/src/linux/module.h:9,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from /usr/src/asm/percpu.h:45,
from /usr/src/asm/current.h:5,
from /usr/src/asm/processor.h:15,
from /usr/src/linux/prefetch.h:14,
from /usr/src/linux/list.h:6,
from /usr/src/linux/module.h:9,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/kernel.h:182: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:186: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:190: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:194: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:198: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:262: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:264: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux/kernel.h:532: error: expected declaration specifiers or ‘...’ before ‘va_list’
In file included from /usr/src/linux/prefetch.h:14,
from /usr/src/linux/list.h:6,
from /usr/src/linux/module.h:9,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/asm/processor.h:161:1: warning: "cache_line_size" redefined
In file included from /usr/src/asm/processor.h:28,
from /usr/src/linux/prefetch.h:14,
from /usr/src/linux/list.h:6,
from /usr/src/linux/module.h:9,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/cache.h:64:1: warning: this is the location of the previous definition
In file included from /usr/src/linux/prefetch.h:14,
from /usr/src/linux/list.h:6,
from /usr/src/linux/module.h:9,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/asm/processor.h: In function ‘load_cr3’:
/usr/src/asm/processor.h:192: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/asm/processor.h:192: error: (Each undeclared identifier is reported only once
/usr/src/asm/processor.h:192: error: for each function it appears in.)
/usr/src/asm/processor.h: In function ‘wbinvd_halt’:
/usr/src/asm/processor.h:767: error: implicit declaration of function ‘halt’
In file included from /usr/src/asm/atomic.h:4,
from /usr/src/asm/thread_info.h:24,
from /usr/src/linux/thread_info.h:56,
from /usr/src/linux/preempt.h:9,
from /usr/src/linux/spinlock.h:50,
from /usr/src/linux/seqlock.h:29,
from /usr/src/linux/time.h:8,
from /usr/src/linux/stat.h:60,
from /usr/src/linux/module.h:10,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:201: warning: type defaults to ‘int’ in declaration of ‘atomic64_t’
/usr/src/asm/atomic_64.h:201: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:213: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:225: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_add’:
/usr/src/asm/atomic_64.h:228: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:227: error: invalid lvalue in asm output 0
/usr/src/asm/atomic_64.h:227: error: memory input 2 is not directly addressable
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:239: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_sub’:
/usr/src/asm/atomic_64.h:242: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:241: error: invalid lvalue in asm output 0
/usr/src/asm/atomic_64.h:241: error: memory input 2 is not directly addressable
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:255: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_sub_and_test’:
/usr/src/asm/atomic_64.h:260: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:259: error: invalid lvalue in asm output 0
/usr/src/asm/atomic_64.h:259: error: memory input 3 is not directly addressable
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:271: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:284: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:299: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:317: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:336: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_add_negative’:
/usr/src/asm/atomic_64.h:341: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:340: error: invalid lvalue in asm output 0
/usr/src/asm/atomic_64.h:340: error: memory input 3 is not directly addressable
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:353: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_add_return’:
/usr/src/asm/atomic_64.h:357: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:356: error: invalid lvalue in asm output 1
/usr/src/asm/atomic_64.h:356: error: memory input 3 is not directly addressable
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:362: error: expected declaration specifiers or ‘...’ before ‘atomic64_t’
/usr/src/asm/atomic_64.h: In function ‘atomic64_sub_return’:
/usr/src/asm/atomic_64.h:364: error: ‘v’ undeclared (first use in this function)
/usr/src/asm/atomic_64.h:364: error: too many arguments to function ‘atomic64_add_return’
/usr/src/asm/atomic_64.h: At top level:
/usr/src/asm/atomic_64.h:370: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:375: error: expected ‘)’ before ‘*’ token
/usr/src/asm/atomic_64.h:425: error: expected ‘)’ before ‘*’ token
In file included from /usr/src/linux/mmzone.h:16,
from /usr/src/linux/gfp.h:4,
from /usr/src/linux/kmod.h:22,
from /usr/src/linux/module.h:13,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/nodemask.h: In function ‘__first_node’:
/usr/src/linux/nodemask.h:239: error: implicit declaration of function ‘find_first_bit’
/usr/src/linux/nodemask.h: In function ‘__next_node’:
/usr/src/linux/nodemask.h:245: error: implicit declaration of function ‘find_next_bit’
/usr/src/linux/nodemask.h: In function ‘__first_unset_node’:
/usr/src/linux/nodemask.h:263: error: implicit declaration of function ‘find_first_zero_bit’
In file included from /usr/src/linux/gfp.h:4,
from /usr/src/linux/kmod.h:22,
from /usr/src/linux/module.h:13,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
/usr/src/linux/mmzone.h:251:5: warning: "MAX_NR_ZONES" is not defined
/usr/src/linux/mmzone.h:253:7: warning: "MAX_NR_ZONES" is not defined
/usr/src/linux/mmzone.h:255:7: warning: "MAX_NR_ZONES" is not defined
In file included from /usr/src/linux/gfp.h:4,
from /usr/src/linux/kmod.h:22,
from /usr/src/linux/module.h:13,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/mmzone.h: At top level:
/usr/src/linux/mmzone.h:288: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from /usr/src/linux/gfp.h:8,
from /usr/src/linux/kmod.h:22,
from /usr/src/linux/module.h:13,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/mmdebug.h:4:28: error: linux/autoconf.h: No such file or directory
In file included from /usr/src/linux/elf.h:7,
from /usr/src/linux/module.h:14,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/asm/elf.h: In function ‘start_ia32_thread’:
/usr/src/asm/elf.h:165: error: implicit declaration of function ‘load_gs_index’
/usr/src/asm/elf.h: In function ‘elf_common_init’:
/usr/src/asm/elf.h:178: error: ‘struct pt_regs’ has no member named ‘r8’
/usr/src/asm/elf.h:178: error: ‘struct pt_regs’ has no member named ‘r9’
/usr/src/asm/elf.h:178: error: ‘struct pt_regs’ has no member named ‘r10’
/usr/src/asm/elf.h:178: error: ‘struct pt_regs’ has no member named ‘r11’
/usr/src/asm/elf.h:179: error: ‘struct pt_regs’ has no member named ‘r12’
/usr/src/asm/elf.h:179: error: ‘struct pt_regs’ has no member named ‘r13’
/usr/src/asm/elf.h:179: error: ‘struct pt_regs’ has no member named ‘r14’
/usr/src/asm/elf.h:179: error: ‘struct pt_regs’ has no member named ‘r15’
/usr/src/asm/elf.h:180: error: ‘struct thread_struct’ has no member named ‘fs’
In file included from /usr/src/linux/module.h:16,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/kobject.h: At top level:
/usr/src/linux/kobject.h:77: error: expected declaration specifiers or ‘...’ before ‘va_list’
In file included from /usr/src/linux/module.h:18,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/marker.h:34: error: expected declaration specifiers or ‘...’ before ‘va_list’
In file included from /usr/src/linux/tracepoint.h:18,
from /usr/src/linux/module.h:19,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/rcupdate.h:64:2: error: #error "Unknown RCU implementation specified to kernel configuration"
In file included from /usr/src/linux/module.h:19,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/tracepoint.h: In function ‘tracepoint_synchronize_unregister’:
/usr/src/linux/tracepoint.h:156: error: implicit declaration of function ‘__synchronize_sched’
In file included from /usr/src/linux/slab_def.h:17,
from /usr/src/linux/slab.h:166,
from /usr/src/linux/percpu.h:5,
from /usr/src/asm/local.h:4,
from /usr/src/linux/module.h:20,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/kmemtrace.h:12:31: error: trace/events/kmem.h: No such file or directory
In file included from /usr/src/linux/slab.h:166,
from /usr/src/linux/percpu.h:5,
from /usr/src/asm/local.h:4,
from /usr/src/linux/module.h:20,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/linux/slab_def.h: In function ‘kmalloc’:
/usr/src/linux/slab_def.h:157: error: implicit declaration of function ‘trace_kmalloc’
In file included from /usr/src/linux/module.h:22,
from /home/test/test_project/test-001/src/shuttle_usbat.c:45:
/usr/src/asm/module.h:68:2: error: #error unknown processor family
In file included from /usr/src/linux/cdrom.h:913,
from /home/test/test_project/test-001/src/shuttle_usbat.c:47:
/usr/src/linux/device.h: At top level:
/usr/src/linux/device.h:522: error: expected declaration specifiers or ‘...’ before ‘va_list’
In file included from /usr/src/linux/mm.h:14,
from /usr/src/linux/scatterlist.h:6,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/linux/mm_types.h:27:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
/usr/src/linux/mm_types.h:71:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from /usr/src/linux/mm.h:38,
from /usr/src/linux/scatterlist.h:6,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/asm/pgtable.h: In function ‘pmd_page_vaddr’:
/usr/src/asm/pgtable.h:347: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/asm/pgtable.h: In function ‘pud_page_vaddr’:
/usr/src/asm/pgtable.h:418: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/asm/pgtable.h: In function ‘pgd_page_vaddr’:
/usr/src/asm/pgtable.h:463: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
In file included from /usr/src/linux/scatterlist.h:6,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/linux/mm.h: In function ‘virt_to_head_page’:
/usr/src/linux/mm.h:308: error: implicit declaration of function ‘__pfn_to_page’
/usr/src/linux/mm.h:308: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/linux/mm.h:308: warning: initialization makes pointer from integer without a cast
In file included from /usr/src/linux/scatterlist.h:6,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/linux/mm.h:444:63: warning: "NR_PAGEFLAGS" is not defined
/usr/src/linux/mm.h:492:62: warning: "NR_PAGEFLAGS" is not defined
In file included from /usr/src/linux/scatterlist.h:6,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/linux/mm.h: In function ‘lowmem_page_address’:
/usr/src/linux/mm.h:582: error: implicit declaration of function ‘__page_to_pfn’
/usr/src/linux/mm.h:582: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/linux/mm.h:919:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from /usr/src/linux/scatterlist.h:8,
from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/asm/io.h: In function ‘virt_to_phys’:
/usr/src/asm/io.h:99: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/asm/io.h: In function ‘phys_to_virt’:
/usr/src/asm/io.h:117: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
In file included from /usr/src/linux/dma-mapping.h:7,
from /usr/src/scsi/scsi_cmnd.h:4,
from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/linux/scatterlist.h: In function ‘sg_set_buf’:
/usr/src/linux/scatterlist.h:112: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/usr/src/linux/scatterlist.h:112: warning: passing argument 2 of ‘sg_set_page’ makes pointer from integer without a cast
/usr/src/linux/scatterlist.h:85: note: expected ‘struct page *’ but argument is of type ‘int’
In file included from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/scsi/scsi_cmnd.h:27:25: warning: "BLK_MAX_CDB" is not defined
/usr/src/scsi/scsi_cmnd.h:28:3: error: #error MAX_COMMAND_SIZE can not be bigger than BLK_MAX_CDB
In file included from /home/test/test_project/test-001/src/shuttle_usbat.c:50:
/usr/src/scsi/scsi_cmnd.h: In function ‘scsi_bidi_cmnd’:
/usr/src/scsi/scsi_cmnd.h:184: error: implicit declaration of function ‘blk_bidi_rq’
/usr/src/scsi/scsi_cmnd.h:185: error: dereferencing pointer to incomplete type
/usr/src/scsi/scsi_cmnd.h: In function ‘scsi_in’:
/usr/src/scsi/scsi_cmnd.h:191: error: dereferencing pointer to incomplete type
/usr/src/scsi/scsi_cmnd.h: In function ‘scsi_get_lba’:
/usr/src/scsi/scsi_cmnd.h:273: error: implicit declaration of function ‘blk_rq_pos’
In file included from /usr/src/linux/sched.h:77,
from /usr/src/linux/interrupt.h:13,
from /usr/src/linux/usb.h:15,
from /usr/src/storage/usb.h:45,
from /home/test/test_project/test-001/src/shuttle_usbat.c:52:
/usr/src/linux/proportions.h: In function ‘prop_inc_percpu’:
/usr/src/linux/proportions.h:75: error: implicit declaration of function ‘local_irq_save’
/usr/src/linux/proportions.h:77: error: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux/interrupt.h:13,
from /usr/src/linux/usb.h:15,
from /usr/src/storage/usb.h:45,
from /home/test/test_project/test-001/src/shuttle_usbat.c:52:
/usr/src/linux/sched.h:381:5: warning: "CONFIG_SPLIT_PTLOCK_CPUS" is not defined
In file included from /usr/src/storage/usb.h:45,
from /home/test/test_project/test-001/src/shuttle_usbat.c:52:
/usr/src/linux/usb.h: In function ‘usb_register’:
/usr/src/linux/usb.h:949: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
/home/test/test_project/test-001/src/shuttle_usbat.c:174:28: error: unusual_usbat.h: No such file or directory
make[2]: *** [test_001-shuttle_usbat.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
make[2]: Leaving directory `/home/test/test_project/test-001/Debug/src'
make[2]: Leaving directory `/home/test/test_project/test-001/Debug/src'
make[1]: Leaving directory `/home/test/test_project/test-001/Debug'
make[1]: Leaving directory `/home/test/test_project/test-001/Debug'
Completed unsuccessfully
Total time taken: 2 secs

---

