---
title: "monodevelop problem"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by ylw33 on 2008-08-30
hi all
i m very new to this linux. i have started this a week before.
since i need to develop some c# programs, i installed monodevelop from synaptic package manager.

till this , i find no trouble.
then on opening monodevelp from prgramming->monodevelop, its loading for a while. then it disappears.

can anyone say me, whats the problem
------
i did what u say.

here is the summary. i cant get anything from this. home@home-desktop:~$ monodevelop
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

** (./MonoDevelop.exe:13802): CRITICAL **: _wapi_shm_file_open: shared file [/home/home/.wapi/shared_data-home-desktop-Linux-i686-312-11-0] write error: No space left on device

** (./MonoDevelop.exe:13802): CRITICAL **: _wapi_shm_attach: shared file [/home/home/.wapi/shared_data-home-desktop-Linux-i686-312-11-0] open error
**
** ERROR:(shared.c:346):shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (./MonoDevelop.exe:13802): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (./MonoDevelop.exe:13802): WARNING **: Thread (nil) may have been prematurely finalized

** (./MonoDevelop.exe:13802): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	monodevelop [0x816b1fa]
	[0xb7ef7440]
	/lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7cc2a01]
	/usr/lib/libglib-2.0.so.0(g_assertion_message+0x121) [0xb7e82751]
	/usr/lib/libglib-2.0.so.0 [0xb7e82cad]
	monodevelop [0x811703e]
	monodevelop [0x8109342]
	monodevelop(mono_once+0x96) [0x8112726]
	monodevelop [0x810907c]
	monodevelop [0x8115f6e]
	monodevelop [0x8116364]
	monodevelop [0x80d1877]
	monodevelop(mono_runtime_init+0x26) [0x80d8836]
	monodevelop [0x8134535]
	monodevelop(mono_main+0x3aa) [0x805a9da]
	monodevelop [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cac450]
	monodevelop [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c54940 (LWP 13802)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7ef7410 in __kernel_vsyscall ()
  1 Thread 0xb7c54940 (LWP 13802)  0xb7ef7410 in __kernel_vsyscall ()

Thread 1 (Thread 0xb7c54940 (LWP 13802)):
#0  0xb7ef7410 in __kernel_vsyscall ()
#1  0xb7d2bd89 in fork () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e19034 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7e93589 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7e941ad in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7e9466c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0816b295 in ?? ()
#7  <signal handler called>
#8  0xb7ef7410 in __kernel_vsyscall ()
#9  0xb7cc1085 in raise () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7cc2a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#11 0xb7e82751 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#12 0xb7e82cad in g_assertion_message_expr () from /usr/lib/libglib-2.0.so.0
#13 0x0811703e in ?? ()
#14 0x08109342 in ?? ()
#15 0x08112726 in mono_once ()
#16 0x0810907c in ?? ()
#17 0x08115f6e in ?? ()
#18 0x08116364 in ?? ()
#19 0x080d1877 in ?? ()
#20 0x080d8836 in mono_runtime_init ()
#21 0x08134535 in ?? ()
#22 0x0805a9da in mono_main ()
#23 0x0805a122 in ?? ()
#24 0xb7cac450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#25 0x0805a091 in ?? ()
#0  0xb7ef7410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


help me to find a solution

---

### Post by gmxgeek on 2008-08-30
try opening it through the terminal and see if it spits out any errors, then post them here

---

### Post by kellemes on 2008-08-31
Indeed.. open a terminal window and type..
```
monodevelop
```

Watch (and post) the output.

---

