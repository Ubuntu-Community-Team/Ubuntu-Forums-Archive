---
title: "help with monodevelop debugging"
date: 2010-09-14
forum: Programming Talk
---

### Post by Mauri72 on 2010-09-14
Hi all. I am not exactly sure what caused this. I know there was an update from badgerports a little while ago, but I have not done any coding with monodevelop since, so I am not sure whether that was the cause or if it was me who screwed up my laptop some other way. Anyway the issue is that I cannot debug any mono code with monodevelop. Nothing wrong with the code which compiles and runs fine, but , if I add a breakpoint to the project and start debugging (with the debug button, with F5, or from the menu Run with mono soft Degub), the result is a segmentation error as soon as the breakpoint is reached. 
The stacktrace is:

```

Native stacktrace:

    /usr/bin/mono() [0x487afb]
    /usr/bin/mono() [0x4d4bcf]
    /lib/libpthread.so.0(+0xf8f0) [0x7fcc48c858f0]
    /lib/libc.so.6(+0x128acb) [0x7fcc48798acb]
    /usr/bin/mono() [0x41ac23]
    /usr/bin/mono() [0x41e25d]
    /usr/bin/mono() [0x41edf2]
    /usr/bin/mono() [0x41fc04]
    /usr/bin/mono(mono_runtime_invoke+0x4b) [0x4e125b]
    /usr/bin/mono() [0x4a6149]
    /usr/bin/mono() [0x4a6748]
    /usr/bin/mono() [0x4a7205]
    /usr/bin/mono() [0x4a8032]

Debug info from gdb:

Mono support loaded.
Mono support loaded.
[Thread debugging using libthread_db enabled]
[New Thread 0x7fcc45a0f710 (LWP 5138)]
[New Thread 0x7fcc45c10710 (LWP 5137)]
[New Thread 0x7fcc497c3710 (LWP 5136)]
[New Thread 0x7fcc4743f710 (LWP 5134)]
[New Thread 0x7fcc47c40710 (LWP 5133)]
[New Thread 0x7fcc48441710 (LWP 5132)]
0x00007fcc48c8493d in read () from /lib/libpthread.so.0
  7 Thread 0x7fcc48441710 (LWP 5132)  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  6 Thread 0x7fcc47c40710 (LWP 5133)  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  5 Thread 0x7fcc4743f710 (LWP 5134)  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  4 Thread 0x7fcc497c3710 (LWP 5136)  0x00007fcc48c8511d in nanosleep ()
   from /lib/libpthread.so.0
  3 Thread 0x7fcc45c10710 (LWP 5137)  0x00007fcc48c83b50 in sem_wait ()
   from /lib/libpthread.so.0
  2 Thread 0x7fcc45a0f710 (LWP 5138)  0x00007fcc48c84d3c in recv ()
   from /lib/libpthread.so.0
* 1 Thread 0x7fcc49978740 (LWP 5131)  0x00007fcc48c8493d in read ()
   from /lib/libpthread.so.0

Thread 7 (Thread 0x7fcc48441710 (LWP 5132)):
#0  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#5  0x00007fcc487566fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7fcc47c40710 (LWP 5133)):
#0  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#5  0x00007fcc487566fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7fcc4743f710 (LWP 5134)):
#0  0x00007fcc48c8185c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#5  0x00007fcc487566fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7fcc497c3710 (LWP 5136)):
#0  0x00007fcc48c8511d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005934d2 in collection_thread (unused=<value optimised out>)
    at collection.c:34
#2  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#3  0x00007fcc487566fd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7fcc45c10710 (LWP 5137)):
#0  0x00007fcc48c83b50 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000005a6bc8 in mono_sem_wait (sem=0x8bbf60, alertable=0)
    at mono-semaphore.c:102
#2  0x00000000005218da in finalizer_thread (unused=<value optimised out>)
    at gc.c:1022
#3  0x0000000000535598 in start_wrapper (data=<value optimised out>)
    at threads.c:666
#4  0x0000000000599ff3 in thread_start_routine (args=0x249a1f0)
    at wthreads.c:286
#5  0x00000000005c2d01 in GC_start_routine (arg=<value optimised out>)
    at pthread_support.c:1390
#6  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#7  0x00007fcc487566fd in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7fcc45a0f710 (LWP 5138)):
#0  0x00007fcc48c84d3c in recv () from /lib/libpthread.so.0
#1  0x00000000004a23ae in recv (fd=3, buf=0x7fcc45a0ed50, len=11, 
    flags=<value optimised out>) at /usr/include/bits/socket2.h:45
#2  recv_length (fd=3, buf=0x7fcc45a0ed50, len=11, 
    flags=<value optimised out>) at debugger-agent.c:948
#3  0x00000000004add63 in debugger_thread (arg=<value optimised out>)
    at debugger-agent.c:6452
#4  0x0000000000599ff3 in thread_start_routine (args=0x249a380)
    at wthreads.c:286
#5  0x00000000005c2d01 in GC_start_routine (arg=<value optimised out>)
    at pthread_support.c:1390
#6  0x00007fcc48c7c9ca in start_thread () from /lib/libpthread.so.0
#7  0x00007fcc487566fd in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fcc49978740 (LWP 5131)):
#0  0x00007fcc48c8493d in read () from /lib/libpthread.so.0
#1  0x0000000000487c88 in read (signal=<value optimised out>, 
    ctx=<value optimised out>) at /usr/include/bits/unistd.h:45
#2  mono_handle_native_sigsegv (signal=<value optimised out>, 
    ctx=<value optimised out>) at mini-exceptions.c:1818
#3  0x00000000004d4bcf in mono_arch_handle_altstack_exception (sigctx=
    0x7fcc497fac40, fault_addr=<value optimised out>, stack_ovf=0)
    at exceptions-amd64.c:965
#4  <signal handler called>
#5  0x00007fcc48798acb in ?? () from /lib/libc.so.6
#6  0x000000000041ac23 in mono_postprocess_patches (cfg=0x2513590)
    at mini.c:2963
#7  mono_codegen (cfg=0x2513590) at mini.c:3117
#8  0x000000000041e25d in mini_method_compile (method=
    "System.Type:GetType ()", opts=<value optimised out>, 
    domain=<value optimised out>, run_cctors=<value optimised out>, 
    compile_aot=<value optimised out>, parts=<value optimised out>)
    at mini.c:3889
#9  0x000000000041edf2 in mono_jit_compile_method_inner (method=
    "System.Type:GetType ()", opt=55667071, ex=0x7fff1c23eba0) at mini.c:4223
#10 mono_jit_compile_method_with_opt (method="System.Type:GetType ()", opt=
    55667071, ex=0x7fff1c23eba0) at mini.c:4430
#11 0x000000000041fc04 in mono_jit_runtime_invoke (method=
    "System.Type:GetType ()", obj=0x0, params=<value optimised out>, exc=
    0x7fff1c23ef20) at mini.c:4628
#12 0x00000000004e125b in mono_runtime_invoke (method=
    "System.Type:GetType ()", obj=0x0, params=0x7fff1c23ed30, exc=
    0x7fff1c23ef20) at object.c:2613
#13 0x00000000004a6149 in do_invoke_method (tls=<value optimised out>, 
    buf=<value optimised out>, invoke=0x25133a0) at debugger-agent.c:4561
#14 0x00000000004a6748 in invoke_method () at debugger-agent.c:4639
#15 suspend_current () at debugger-agent.c:2253
#16 0x00000000004a7205 in process_event (event=EVENT_KIND_BREAKPOINT, 
    arg=<value optimised out>, il_offset=<value optimised out>, 
    ctx=<value optimised out>, events=0x2458290, suspend_policy=2)
    at debugger-agent.c:2728
#17 0x00000000004a8032 in process_breakpoint_inner () at debugger-agent.c:3486
#18 process_breakpoint () at debugger-agent.c:3502
#19 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```Has anyone got any idea of what maybe going wrong?
Cheers
Maurizio

---

### Post by Mauri72 on 2010-09-14
even a simple helloworld application gives this output when it hits a breakpoint
```
Stacktrace:

  at helloworld.MainClass.Main (string[]) [0x0000a] in /home/maurizio/Projects/helloworld/helloworld/Main.cs:10
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <IL 0x0001d, 0x000c8>

Native stacktrace:

    /usr/bin/mono() [0x487afb]
    /usr/bin/mono() [0x4d4bcf]
    /lib/libpthread.so.0(+0xf8f0) [0x7f1b152408f0]
    /lib/libc.so.6(+0x128acb) [0x7f1b14d53acb]
    /usr/bin/mono() [0x41ac23]
    /usr/bin/mono() [0x41e25d]
    /usr/bin/mono() [0x41edf2]
    /usr/bin/mono() [0x41fc04]
    /usr/bin/mono(mono_runtime_invoke+0x4b) [0x4e125b]
    /usr/bin/mono() [0x4a6149]
    /usr/bin/mono() [0x4a6748]
    /usr/bin/mono() [0x4a7205]
    /usr/bin/mono() [0x4a8032]
    [0x7f1b15d71fa0]

Debug info from gdb:

Mono support loaded.
Mono support loaded.
[Thread debugging using libthread_db enabled]
[New Thread 0x7f1b11fda710 (LWP 6509)]
[New Thread 0x7f1b121db710 (LWP 6508)]
[New Thread 0x7f1b15d87710 (LWP 6507)]
[New Thread 0x7f1b139fa710 (LWP 6505)]
[New Thread 0x7f1b141fb710 (LWP 6504)]
[New Thread 0x7f1b149fc710 (LWP 6503)]
0x00007f1b1523f93d in read () from /lib/libpthread.so.0
  7 Thread 0x7f1b149fc710 (LWP 6503)  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  6 Thread 0x7f1b141fb710 (LWP 6504)  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  5 Thread 0x7f1b139fa710 (LWP 6505)  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  4 Thread 0x7f1b15d87710 (LWP 6507)  0x00007f1b1524011d in nanosleep ()
   from /lib/libpthread.so.0
  3 Thread 0x7f1b121db710 (LWP 6508)  0x00007f1b1523eb50 in sem_wait ()
   from /lib/libpthread.so.0
  2 Thread 0x7f1b11fda710 (LWP 6509)  0x00007f1b1523fd3c in recv ()
   from /lib/libpthread.so.0
* 1 Thread 0x7f1b15f33740 (LWP 6502)  0x00007f1b1523f93d in read ()
   from /lib/libpthread.so.0

Thread 7 (Thread 0x7f1b149fc710 (LWP 6503)):
#0  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#5  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7f1b141fb710 (LWP 6504)):
#0  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#5  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f1b139fa710 (LWP 6505)):
#0  0x00007f1b1523c85c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000005c1823 in GC_wait_marker () at pthread_support.c:1785
#2  0x00000000005ba3bd in GC_help_marker (my_mark_no=1) at mark.c:1116
#3  0x00000000005c262c in GC_mark_thread (id=<value optimised out>)
    at pthread_support.c:548
#4  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#5  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f1b15d87710 (LWP 6507)):
#0  0x00007f1b1524011d in nanosleep () from /lib/libpthread.so.0
#1  0x00000000005934d2 in collection_thread (unused=<value optimised out>)
    at collection.c:34
#2  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#3  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f1b121db710 (LWP 6508)):
#0  0x00007f1b1523eb50 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000005a6bc8 in mono_sem_wait (sem=0x8bbf60, alertable=0)
    at mono-semaphore.c:102
#2  0x00000000005218da in finalizer_thread (unused=<value optimised out>)
    at gc.c:1022
#3  0x0000000000535598 in start_wrapper (data=<value optimised out>)
    at threads.c:666
#4  0x0000000000599ff3 in thread_start_routine (args=0x1ffa358)
    at wthreads.c:286
#5  0x00000000005c2d01 in GC_start_routine (arg=<value optimised out>)
    at pthread_support.c:1390
#6  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f1b11fda710 (LWP 6509)):
#0  0x00007f1b1523fd3c in recv () from /lib/libpthread.so.0
#1  0x00000000004a23ae in recv (fd=3, buf=0x7f1b11fd9d50, len=11, 
    flags=<value optimised out>) at /usr/include/bits/socket2.h:45
#2  recv_length (fd=3, buf=0x7f1b11fd9d50, len=11, flags=<value optimised out>)
    at debugger-agent.c:948
#3  0x00000000004add63 in debugger_thread (arg=<value optimised out>)
    at debugger-agent.c:6452
#4  0x0000000000599ff3 in thread_start_routine (args=0x1ffa4e8)
    at wthreads.c:286
#5  0x00000000005c2d01 in GC_start_routine (arg=<value optimised out>)
    at pthread_support.c:1390
#6  0x00007f1b152379ca in start_thread () from /lib/libpthread.so.0
#7  0x00007f1b14d116fd in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f1b15f33740 (LWP 6502)):
#0  0x00007f1b1523f93d in read () from /lib/libpthread.so.0
#1  0x0000000000487c88 in read (signal=<value optimised out>, 
    ctx=<value optimised out>) at /usr/include/bits/unistd.h:45
#2  mono_handle_native_sigsegv (signal=<value optimised out>, 
    ctx=<value optimised out>) at mini-exceptions.c:1818
#3  0x00000000004d4bcf in mono_arch_handle_altstack_exception (sigctx=
    0x7f1b15db5c40, fault_addr=<value optimised out>, stack_ovf=0)
    at exceptions-amd64.c:965
#4  <signal handler called>
#5  0x00007f1b14d53acb in ?? () from /lib/libc.so.6
#6  0x000000000041ac23 in mono_postprocess_patches (cfg=0x7f1b0c00e230)
    at mini.c:2963
#7  mono_codegen (cfg=0x7f1b0c00e230) at mini.c:3117
#8  0x000000000041e25d in mini_method_compile (method=
    "System.Type:GetType ()", opts=<value optimised out>, 
    domain=<value optimised out>, run_cctors=<value optimised out>, 
    compile_aot=<value optimised out>, parts=<value optimised out>)
    at mini.c:3889
#9  0x000000000041edf2 in mono_jit_compile_method_inner (method=
    "System.Type:GetType ()", opt=55667071, ex=0x7fffcaccd5d0) at mini.c:4223
#10 mono_jit_compile_method_with_opt (method="System.Type:GetType ()", opt=
    55667071, ex=0x7fffcaccd5d0) at mini.c:4430
#11 0x000000000041fc04 in mono_jit_runtime_invoke (method=
    "System.Type:GetType ()", obj=0x0, params=<value optimised out>, exc=
    0x7fffcaccd950) at mini.c:4628
#12 0x00000000004e125b in mono_runtime_invoke (method=
    "System.Type:GetType ()", obj=0x0, params=0x7fffcaccd760, exc=
    0x7fffcaccd950) at object.c:2613
#13 0x00000000004a6149 in do_invoke_method (tls=<value optimised out>, 
    buf=<value optimised out>, invoke=0x204a110) at debugger-agent.c:4561
#14 0x00000000004a6748 in invoke_method () at debugger-agent.c:4639
#15 suspend_current () at debugger-agent.c:2253
#16 0x00000000004a7205 in process_event (event=EVENT_KIND_BREAKPOINT, 
    arg=<value optimised out>, il_offset=<value optimised out>, 
    ctx=<value optimised out>, events=0x1fb8070, suspend_policy=2)
    at debugger-agent.c:2728
#17 0x00000000004a8032 in process_breakpoint_inner () at debugger-agent.c:3486
#18 process_breakpoint () at debugger-agent.c:3502
#19 0x00007f1b15d71fa0 in ?? ()
#20 0x000000004158b000 in ?? ()
#21 0x00007fffcaccdd70 in ?? ()
#22 0x0000000040d7b649 in ?? ()
#23 0x0000000040d7b510 in ?? ()
#24 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

bash: line 1:  6502 Aborted                 /usr/bin/mono --debug --debugger-agent=transport=dt_socket,address=127.0.0.1:42787 "/home/maurizio/Projects/helloworld/helloworld/bin/Debug/helloworld.exe"

Press any key to continue...

```

all applications run fine in debug mode as long as there are no breakpoints

---

### Post by directhex on 2010-09-15
Some nasty debugging-relating bug fixes recently hit Debian Unstable. At some point I'll upload to badgerports.

---

