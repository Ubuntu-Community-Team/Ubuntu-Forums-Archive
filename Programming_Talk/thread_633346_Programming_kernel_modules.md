---
title: "Programming kernel modules"
date: 2007-12-06
forum: Programming Talk
---

### Post by Mathiasdm on 2007-12-06
Are there any programs I need to install to start kernel programming? I have the kernel headers, gcc, binutils, ...

I seem to be getting the following (seems like gcc can't find the headers?):

```

gcc -c -O speaker.c
speaker.c:12:26: fout: linux/module.h: Bestand of map bestaat niet
speaker.c:14:26: fout: linux/ioport.h: Bestand of map bestaat niet
speaker.c:17:20: fout: asm/io.h: Bestand of map bestaat niet
speaker.c:18:26: fout: asm/uaccess.h: Bestand of map bestaat niet
speaker.c:19:25: fout: linux/timer.h: Bestand of map bestaat niet
speaker.c:53: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘read_speaker’
speaker.c:60: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘write_speaker’
speaker.c:82: let op: ‘struct file’ gedeclareerd binnen parameterlijst
speaker.c:82: let op: het bereik ervan is enkel deze definitie of declaratie, hetgeen waarschijnlijk niet de bedoeling is
speaker.c:82: let op: ‘struct inode’ gedeclareerd binnen parameterlijst
speaker.c: In functie ‘open_speaker’:
speaker.c:83: fout: ‘MOD_IN_USE’ undeclared (first use in this function)
speaker.c:83: fout: (Each undeclared identifier is reported only once
speaker.c:83: fout: for each function it appears in.)
speaker.c:85: fout: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
speaker.c: Op bovenste niveau:
speaker.c:92: let op: ‘struct file’ gedeclareerd binnen parameterlijst
speaker.c:92: let op: ‘struct inode’ gedeclareerd binnen parameterlijst
speaker.c: In functie ‘close_speaker’:
speaker.c:93: fout: ‘MOD_IN_USE’ undeclared (first use in this function)
speaker.c: In functie ‘silence’:
speaker.c:104: fout: invalid use of undefined type ‘struct timer_list’
speaker.c:107: fout: invalid use of undefined type ‘struct timer_list’
speaker.c:107: fout: ‘jiffies’ undeclared (first use in this function)
speaker.c: In functie ‘play_next_note’:
speaker.c:118: fout: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
speaker.c:126: fout: invalid use of undefined type ‘struct timer_list’
speaker.c:127: fout: invalid use of undefined type ‘struct timer_list’
speaker.c:127: fout: ‘jiffies’ undeclared (first use in this function)
speaker.c: Op bovenste niveau:
speaker.c:137: fout: variabele ‘speaker_fops’ heeft beginwaarde, maar een onvolledig type
speaker.c:138: fout: unknown field ‘read’ specified in initializer
speaker.c:138: fout: ‘read_speaker’ undeclared here (not in a function)
speaker.c:138: let op: overtollige elementen in beginwaarde van struct
speaker.c:138: let op: (near initialization for ‘speaker_fops’)
speaker.c:139: fout: unknown field ‘write’ specified in initializer
speaker.c:139: fout: ‘write_speaker’ undeclared here (not in a function)
speaker.c:139: let op: overtollige elementen in beginwaarde van struct
speaker.c:139: let op: (near initialization for ‘speaker_fops’)
speaker.c:140: fout: unknown field ‘open’ specified in initializer
speaker.c:140: let op: overtollige elementen in beginwaarde van struct
speaker.c:140: let op: (near initialization for ‘speaker_fops’)
speaker.c:141: fout: unknown field ‘release’ specified in initializer
speaker.c:141: let op: overtollige elementen in beginwaarde van struct
speaker.c:141: let op: (near initialization for ‘speaker_fops’)
speaker.c: In functie ‘cleanup_module’:
speaker.c:165: fout: ‘MOD_IN_USE’ undeclared (first use in this function)


```
Basically, it can't find any of the headers I included.

---

### Post by pmasiar on 2007-12-06
Did you installed build-essentials? This should be FAQ, read sticky.

---

### Post by geraldm on 2007-12-06
>Basically, it can't find any of the headers I included.

gcc -c -O speaker.c
You did not include any headers.

The kernel headers that are in /usr/include/linux and /usr/include/asm are the headers used to create libc.so
The headers to be used in the building of a kernel are in the kernel
source, along with the other kernel code.
To build a kernel the gcc command you used will never work. 
In the top directory of the kernel source, read the file README.

Gerald

---

### Post by Mathiasdm on 2007-12-06
Yes, build-essential is installed. Everything required for compiling C programs is installed.

---

### Post by Mathiasdm on 2007-12-06
> **geraldm said:**
> >Basically, it can't find any of the headers I included.

gcc -c -O speaker.c
You did not include any headers.

The kernel headers that are in /usr/include/linux and /usr/include/asm are the headers used to create libc.so
The headers to be used in the building of a kernel are in the kernel
source, along with the other kernel code.
To build a kernel the gcc command you used will never work. 
In the top directory of the kernel source, read the file README.

Gerald

Ah, I didn't know that.
I had a class today, in which we compiled the same module, with the gcc -c -O speaker.c command, and it worked fine. I assumed it would be the same here.

---

### Post by Mathiasdm on 2007-12-06
Okay, I checked /usr/src/linux-headers-2.6.22-14, and there's no README file there. I also tried various includes with gcc, and they all seem to fail.
I'm kinda lost here, I'm afraid.
Any hints?

@pmasiar: a slightly kinder response would have been nice. The stickies don't seem to have any information on compiling kernel modules.

Edit: Okay, I'm having a look at /usr/src/linux-source-2.6.22 now.

---

### Post by Mathiasdm on 2007-12-06
I think I'm getting closer (though I haven't managed to compile the module yet).

The command:
```

 gcc -c -O -Wall -D__KERNEL__ -DMODULE -I /usr/src/linux-headers-2.6.22-14/include/ speaker.c 2> ~/log
```

The output:
```

speaker.c:9:1: let op: "__KERNEL__" opnieuw gedefinieerd
<commandolijn>:1:1: let op: dit is de locatie van de eerdere definitie
speaker.c:10:1: let op: "MODULE" opnieuw gedefinieerd
<commandolijn>:1:1: let op: dit is de locatie van de eerdere definitie
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9:24: fout: asm/bitops.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In functie ‘get_bitmask_order’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:15: let op: impliciete declaratie van functie ‘fls’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In functie ‘hweight_long’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: let op: impliciete declaratie van functie ‘hweight32’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: let op: impliciete declaratie van functie ‘hweight64’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In functie ‘fls_long’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:58: let op: impliciete declaratie van functie ‘fls64’
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:21:29: fout: asm/thread_info.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:30: let op: ‘struct thread_info’ gedeclareerd binnen parameterlijst
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:30: let op: het bereik ervan is enkel deze definitie of declaratie, hetgeen waarschijnlijk niet de bedoeling is
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In functie ‘set_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:32: let op: impliciete declaratie van functie ‘set_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:32: fout: dereferentie van pointer naar onvolledig type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:35: let op: ‘struct thread_info’ gedeclareerd binnen parameterlijst
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In functie ‘clear_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:37: let op: impliciete declaratie van functie ‘clear_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:37: fout: dereferentie van pointer naar onvolledig type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:40: let op: ‘struct thread_info’ gedeclareerd binnen parameterlijst
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In functie ‘test_and_set_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:42: let op: impliciete declaratie van functie ‘test_and_set_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:42: fout: dereferentie van pointer naar onvolledig type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:45: let op: ‘struct thread_info’ gedeclareerd binnen parameterlijst
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In functie ‘test_and_clear_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:47: let op: impliciete declaratie van functie ‘test_and_clear_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:47: fout: dereferentie van pointer naar onvolledig type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:50: let op: ‘struct thread_info’ gedeclareerd binnen parameterlijst
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In functie ‘test_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:52: let op: impliciete declaratie van functie ‘test_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:52: fout: dereferentie van pointer naar onvolledig type
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:10,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/linkage.h:4:25: fout: asm/linkage.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:16,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:53,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/log2.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/log2.h:52: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_power_of_2’
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:53,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:18:21: fout: asm/bug.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:53,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:125: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:126: fout: format string argument not a string type
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:126: let op: conflicting types for built-in function ‘snprintf’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:127: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:128: let op: conflicting types for built-in function ‘vsnprintf’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:129: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:130: fout: format string argument not a string type
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:131: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:172: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘printk_timed_ratelimit’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:221: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:223: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:223: fout: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:226: fout: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:226: fout: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:228: fout: expected declaration specifiers or ‘...’ before ‘size_t’
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:57:24: fout: asm/system.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:290: fout: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: In functie ‘double_spin_lock’:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: fout: ‘l1_first’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: fout: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:294: fout: for each function it appears in.)
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:309: fout: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: In functie ‘double_spin_unlock’:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:313: fout: ‘l1_taken_first’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326:24: fout: asm/atomic.h: Bestand of map bestaat niet
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:332: fout: expected ‘)’ before ‘*’ token
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/list.h:8,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/prefetch.h:14:27: fout: asm/processor.h: Bestand of map bestaat niet
/usr/src/linux-headers-2.6.22-14/include/linux/prefetch.h:15:23: fout: asm/cache.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/prefetch.h:58: fout: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/list.h: In functie ‘__list_add_rcu’:
/usr/src/linux-headers-2.6.22-14/include/linux/list.h:100: let op: impliciete declaratie van functie ‘smp_wmb’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/time.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:11,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/seqlock.h: In functie ‘read_seqbegin’:
/usr/src/linux-headers-2.6.22-14/include/linux/seqlock.h:89: let op: impliciete declaratie van functie ‘smp_rmb’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:11,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:13: fout: expected specifier-qualifier-list before ‘time_t’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:19: fout: expected specifier-qualifier-list before ‘time_t’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timespec_equal’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:41: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:41: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:41: fout: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:41: fout: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timespec_compare’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:51: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:51: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:53: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:53: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:55: fout: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:55: fout: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timeval_compare’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:60: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:60: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:62: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:62: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:64: fout: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:64: fout: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:71: fout: expected declaration specifiers or ‘...’ before ‘time_t’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timespec_sub’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:80: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:80: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:81: fout: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:81: fout: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:81: fout: too many arguments to function ‘set_normalized_timespec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘get_seconds’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:100: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timespec_to_ns’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:133: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:133: fout: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timeval_to_ns’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:145: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:146: fout: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h: In functie ‘timespec_add_ns’:
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:172: fout: ‘struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:175: fout: ‘struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/time.h:177: fout: ‘struct timespec’ has no member named ‘tv_nsec’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:11,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/stat.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/stat.h:64: fout: expected specifier-qualifier-list before ‘dev_t’
In bestand ingevoegd door /usr/include/asm/ptrace.h:7,
                 door /usr/src/linux-headers-2.6.22-14/include/asm-i386/elf.h:8,
                 door /usr/include/asm/elf.h:7,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/elf.h:7,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:15,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h:32:25: fout: asm/segment.h: Bestand of map bestaat niet
In file included from /usr/include/asm/ptrace.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/asm-i386/elf.h:8,
                 from /usr/include/asm/elf.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:15,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h: In functie ‘user_mode’:
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h:46: fout: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h:46: fout: ‘USER_RPL’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h: In functie ‘user_mode_vm’:
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h:50: fout: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/asm-i386/ptrace.h:50: fout: ‘USER_RPL’ undeclared (first use in this function)
In bestand ingevoegd door /usr/include/asm/elf.h:7,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/elf.h:7,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:15,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/asm-i386/elf.h:50:22: fout: asm/desc.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:22,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/sysfs.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/sysfs.h:26: fout: expected specifier-qualifier-list before ‘mode_t’
/usr/src/linux-headers-2.6.22-14/include/linux/sysfs.h:60: fout: expected specifier-qualifier-list before ‘size_t’
/usr/src/linux-headers-2.6.22-14/include/linux/sysfs.h:69: fout: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.22-14/include/linux/sysfs.h:176: fout: expected declaration specifiers or ‘...’ before ‘mode_t’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:25,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/kref.h:24: fout: expected specifier-qualifier-list before ‘atomic_t’
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:27,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/wait.h:26:25: fout: asm/current.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:254: fout: expected specifier-qualifier-list before ‘ssize_t’
In bestand ingevoegd door speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:19:23: fout: asm/local.h: Bestand of map bestaat niet
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:21:24: fout: asm/module.h: Bestand of map bestaat niet
In file included from speaker.c:12:
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:49: fout: expected specifier-qualifier-list before ‘ssize_t’
speaker.c:17:20: fout: asm/io.h: Bestand of map bestaat niet
speaker.c:18:26: fout: asm/uaccess.h: Bestand of map bestaat niet
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:4,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:25,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 door speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/calc64.h:5:23: fout: asm/div64.h: Bestand of map bestaat niet
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:4,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:25,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 from speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/calc64.h: In functie ‘do_div_llr’:
/usr/src/linux-headers-2.6.22-14/include/linux/calc64.h:25: let op: impliciete declaratie van functie ‘do_div’
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:8,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:25,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 door speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/timex.h:187:23: fout: asm/timex.h: Bestand of map bestaat niet
In bestand ingevoegd door /usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:25,
                 door /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 door speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:33:3: fout: #error You lose.
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:225:31: fout: deling door nul in `#if'
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:25,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 from speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h: Op bovenste niveau:
/usr/src/linux-headers-2.6.22-14/include/linux/jiffies.h:274: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jiffies_to_clock_t’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/timer.h:5,
                 from speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h: In functie ‘timespec_to_ktime’:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:210: fout: ‘const struct timespec’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:211: fout: ‘const struct timespec’ has no member named ‘tv_nsec’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h: In functie ‘timeval_to_ktime’:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:222: fout: ‘const struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:223: fout: ‘const struct timeval’ has no member named ‘tv_usec’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h: In functie ‘ktime_to_timespec’:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:234: fout: unknown field ‘tv_sec’ specified in initializer
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:234: fout: ‘time_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:234: let op: overtollige elementen in beginwaarde van struct
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:234: let op: (near initialization for ‘(anonymous)’)
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:234: fout: expected ‘}’ before ‘kt’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h: In functie ‘ktime_to_timeval’:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:247: fout: unknown field ‘tv_sec’ specified in initializer
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:247: fout: ‘time_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:247: let op: overtollige elementen in beginwaarde van struct
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:247: let op: (near initialization for ‘(anonymous)’)
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:247: fout: expected ‘}’ before ‘kt’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h: In functie ‘ktime_to_us’:
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:279: fout: ‘struct timeval’ has no member named ‘tv_sec’
/usr/src/linux-headers-2.6.22-14/include/linux/ktime.h:279: fout: ‘struct timeval’ has no member named ‘tv_usec’
In file included from speaker.c:19:
/usr/src/linux-headers-2.6.22-14/include/linux/timer.h: In functie ‘add_timer’:
/usr/src/linux-headers-2.6.22-14/include/linux/timer.h:153: let op: impliciete declaratie van functie ‘BUG_ON’
speaker.c: Op bovenste niveau:
speaker.c:41: let op: teruggeeftype krijgt standaardwaarde ‘int’
speaker.c: In functie ‘program_speaker’:
speaker.c:41: let op: impliciete declaratie van functie ‘outb_p’
speaker.c: Op bovenste niveau:
speaker.c:42: let op: teruggeeftype krijgt standaardwaarde ‘int’
speaker.c: In functie ‘speaker_on’:
speaker.c:42: let op: impliciete declaratie van functie ‘inb_p’
speaker.c: Op bovenste niveau:
speaker.c:43: let op: teruggeeftype krijgt standaardwaarde ‘int’
speaker.c:44: let op: teruggeeftype krijgt standaardwaarde ‘int’
speaker.c:53: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘read_speaker’
speaker.c:60: fout: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘write_speaker’
speaker.c:82: let op: ‘struct inode’ gedeclareerd binnen parameterlijst
speaker.c: In functie ‘open_speaker’:
speaker.c:83: fout: ‘MOD_IN_USE’ undeclared (first use in this function)
speaker.c:85: fout: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
speaker.c: Op bovenste niveau:
speaker.c:92: let op: ‘struct inode’ gedeclareerd binnen parameterlijst
speaker.c: In functie ‘close_speaker’:
speaker.c:93: fout: ‘MOD_IN_USE’ undeclared (first use in this function)
speaker.c: In functie ‘play_next_note’:
speaker.c:115: let op: impliciete declaratie van functie ‘next_noot’
speaker.c:118: fout: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
speaker.c:114: let op: unused variable ‘i’
speaker.c: Op bovenste niveau:
speaker.c:137: fout: variabele ‘speaker_fops’ heeft beginwaarde, maar een onvolledig type
speaker.c:138: fout: unknown field ‘read’ specified in initializer
speaker.c:138: fout: ‘read_speaker’ undeclared here (not in a function)
speaker.c:138: let op: overtollige elementen in beginwaarde van struct
speaker.c:138: let op: (near initialization for ‘speaker_fops’)
speaker.c:139: fout: unknown field ‘write’ specified in initializer
speaker.c:139: fout: ‘write_speaker’ undeclared here (not in a function)
speaker.c:139: let op: overtollige elementen in beginwaarde van struct
speaker.c:139: let op: (near initialization for ‘speaker_fops’)
speaker.c:140: fout: unknown field ‘open’ specified in initializer
speaker.c:140: let op: overtollige elementen in beginwaarde van struct
speaker.c:140: let op: (near initialization for ‘speaker_fops’)
speaker.c:141: fout: unknown field ‘release’ specified in initializer
speaker.c:141: let op: overtollige elementen in beginwaarde van struct
speaker.c:141: let op: (near initialization for ‘speaker_fops’)
speaker.c: In functie ‘init_module’:
speaker.c:147: let op: impliciete declaratie van functie ‘register_chrdev’
speaker.c: In functie ‘cleanup_module’:
speaker.c:165: fout: ‘MOD_IN_USE’ undeclared (first use in this function)
speaker.c:166: let op: impliciete declaratie van functie ‘unregister_chrdev’
speaker.c: In functie ‘next_noot’:
speaker.c:179: let op: unused variable ‘mark’
```

---

### Post by geraldm on 2007-12-06
Please excuse my previous post, as I was thinking that you were building the module along with the rest of the kernel source.
The README file is in the vanilla kernel source -- [www.kernel.org](www.kernel.org).
You do not need to look into it if you are not building the whole kernel.

Gerald

---

### Post by ellingsworthorpleton on 2008-06-26
Yea, so I have exactly the same problem. I'm using Ubuntu 8.04. Below are some of my attempts at compiling my program (also listed below):

```
cc -D__KERNEL__ -DMODULE -Wall -I/lib/modules/2.6.24-19-generic/build/include/ -c hello.c

cc -D__KERNEL__ -DMODULE -Wall -I/usr/src/linux-headers-2.6.24-19-generic/include/ -c hello.c
```

hello.c:
```
#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
  printk(KERN_ALERT "Hello, world\n");
  return 0;
}

static void hello_exit(void)
{
  printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);

```

Basically I get the same errors the other guy was getting:
```
cc -D__KERNEL__ -DMODULE -Wall -I/lib/modules/`uname -r`/build/include/ -c hello.c
In file included from /lib/modules/2.6.24-19-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.24-19-generic/build/include/asm/processor_64.h:79: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.24-19-generic/build/include/asm/processor_64.h:79: error: requested alignment is not a constant
/lib/modules/2.6.24-19-generic/build/include/asm/processor_64.h:200: error: requested alignment is not a constant
In file included from /lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:35,
                 from /lib/modules/2.6.24-19-generic/build/include/asm/elf.h:8,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/elf.h:6,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/module.h:14,
                 from hello.c:2:
/lib/modules/2.6.24-19-generic/build/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /lib/modules/2.6.24-19-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/module.h:9,
                 from hello.c:2:
/lib/modules/2.6.24-19-generic/build/include/asm/processor_64.h:29:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.24-19-generic/build/include/asm/elf.h:8,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/elf.h:6,
                 from /lib/modules/2.6.24-19-generic/build/include/linux/module.h:14,
                 from hello.c:2:
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h: In function ‘user_mode’:
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:50: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:50: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:50: error: for each function it appears in.)
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:50: error: ‘USER_RPL’ undeclared (first use in this function)
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:51: warning: control reaches end of non-void function
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h: In function ‘user_mode_vm’:
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:54: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:54: error: ‘USER_RPL’ undeclared (first use in this function)
/lib/modules/2.6.24-19-generic/build/include/asm/ptrace.h:55: warning: control reaches end of non-void function
make: *** [all] Error 1

```

I'm a bit on the new-comer side of things here so if you tell me to replace the dingle arms on the retroencabulator, I probably won't understand what you mean.

Thanks to anyone kind enough to help :)

thorpleton

---

### Post by ellingsworthorpleton on 2008-06-26
ok so after some research it looks like the 2.6 kernel does things a little differently in regard to compiling your own modules. The Makefile that worked was:

obj-m := hello.o

and the command that worked was:

make -C /usr/src/linux-headers-2.6.24-19-generic M=`pwd` modules

Hooray!!!

---

### Post by dwhitney67 on 2008-06-27
As I was reading through the various posts, I was surprised that that it took 9 posts before the solution became apparent!

'gcc' should NOT be used directly to compile kernel modules.  Use the procedure at shown in the previous post, or alternatively create a Makefile that encompasses everything that is required to build the module.  Here's an example:
```
obj-m += hello.o

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```

P.S.  It is always best to use the command 'uname -r' to derive the current kernel version, rather than hard-coding the value.  If a new kernel is added later (or if a different version exists on another platform), and the kernel version number is hard-coded in many scripts and/or Makefiles, it would be a bitch to go back and edit those.

---

