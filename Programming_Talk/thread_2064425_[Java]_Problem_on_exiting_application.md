---
title: "[Java] Problem on exiting application"
date: 2012-09-29
forum: Programming Talk
---

### Post by jadus on 2012-09-29
Hi guys, i am coding new game in Java w/ LWJGL and everything is fine, but when a exit application, Java (OpenJDK and Oracle, i tried both of them) crash in this: 

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f76d4814c58, pid=5950, tid=140148374587136
#
# JRE version: 7.0_07-b10
# Java VM: Java HotSpot(TM) 64-Bit Server VM (23.3-b01 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libX11.so.6+0x33c58]  XQueryExtension+0x28
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.sun.com/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x00007f76e8091800):  VMThread [stack: 0x00007f76d6054000,0x00007f76d6155000] [id=5960]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0xffffffffe8265198

Registers:
RAX=0x00007f76cc0008c0, RBX=0xffffffffe8264830, RCX=0x00007f76d6153878, RDX=0x00007f76d6153874
RSP=0x00007f76d6153810, RBP=0x00007f76aeadb932, RSI=0x00007f76aeadb932, RDI=0xffffffffe8264830
R8 =0x00007f76d615387c, R9 =0x0000000000000000, R10=0x00007f76ee345fa8, R11=0x00007f76edfc7ca0
R12=0x0000000000000000, R13=0x00007f76aeadb932, R14=0x00007f76cc0008c0, R15=0x0000000000000000
RIP=0x00007f76d4814c58, EFLAGS=0x0000000000010202, CSGSFS=0x0000000000000033, ERR=0x0000000000000005
  TRAPNO=0x000000000000000e

Top of Stack: (sp=0x00007f76d6153810)
0x00007f76d6153810:   00007f76edf9a790 00007f76eeb81548
0x00007f76d6153820:   00007f76d6153a10 00007f76d6153a00
0x00007f76d6153830:   00000000ffffffff ffffffffe8264830
0x00007f76d6153840:   00007f76aeadb932 0000000000000000
0x00007f76d6153850:   00007f76aeadb932 00007f76cc0008c0
0x00007f76d6153860:   0000000000000000 00007f76d4808c55
0x00007f76d6153870:   00007f76eeba3048 00007f76aec14520
0x00007f76d6153880:   00007f76aec14520 ffffffffe8264830
0x00007f76d6153890:   00007f76e82b7170 00007f76d4b2202b
0x00007f76d61538a0:   00007f76edf9a790 0000001100000028
0x00007f76d61538b0:   00007f76d6153930 0000000000000000
0x00007f76d61538c0:   00007f76d6153930 ffffffffe8264830
0x00007f76d61538d0:   0000000000000000 00007f76eeba3048
0x00007f76d61538e0:   00007f76aec2dd50 00007f76aea82119
0x00007f76d61538f0:   0000000000000000 0000000000000028
0x00007f76d6153900:   00007f76d6153930 00007f76d6153950
0x00007f76d6153910:   0000000000000000 00007f76eeba3048
0x00007f76d6153920:   00007f76e8263400 00007f76aea78b42
0x00007f76d6153930:   00007f76d6153b00 00007f76aeadb8b1
0x00007f76d6153940:   00007f76d6153b00 00007f76ee98f92d
0x00007f76d6153950:   00007f76eeba42c8 00007f76eeba4858
0x00007f76d6153960:   00007f76eeba1b40 00007f76e80070f0
0x00007f76d6153970:   00007f76e8007c00 00007f76e80075a0
0x00007f76d6153980:   00007f76e8008100 00007f76e800cfc0
0x00007f76d6153990:   00007f76e8249310 00007f76e8248a10
0x00007f76d61539a0:   00007f76e82384b0 00007f76e8238950
0x00007f76d61539b0:   00007f76e8192c00 00007f76e8194700
0x00007f76d61539c0:   00007f76e8194200 00007f76e8190bc0
0x00007f76d61539d0:   00007f76e8249890 00007f76e8193cf0
0x00007f76d61539e0:   00007f76e8249db0 00007f76e8263400
0x00007f76d61539f0:   00007f76e828c420 00007f76e828c9d0
0x00007f76d6153a00:   00007f76e80020b0 00007f76e8001a30 

Instructions: (pc=0x00007f76d4814c58)
0x00007f76d4814c38:   24 d8 48 89 fb 4c 89 64 24 e0 4c 89 6c 24 e8 48
0x00007f76d4814c48:   89 f5 4c 89 74 24 f0 4c 89 7c 24 f8 48 83 ec 58
0x00007f76d4814c58:   48 8b 87 68 09 00 00 49 89 d4 49 89 cd 4d 89 c6
0x00007f76d4814c68:   48 85 c0 74 02 ff 10 ba 08 00 00 00 be 62 00 00 

Register to memory mapping:

RAX=0x00007f76cc0008c0 is an unknown value
RBX=0xffffffffe8264830 is an unknown value
RCX=0x00007f76d6153878 is an unknown value
RDX=0x00007f76d6153874 is an unknown value
RSP=0x00007f76d6153810 is an unknown value
RBP=0x00007f76aeadb932: <offset 0x96932> in /usr/lib/fglrx/libGL.so.1 at 0x00007f76aea45000
RSI=0x00007f76aeadb932: <offset 0x96932> in /usr/lib/fglrx/libGL.so.1 at 0x00007f76aea45000
RDI=0xffffffffe8264830 is an unknown value
R8 =0x00007f76d615387c is an unknown value
R9 =0x0000000000000000 is an unknown value
R10=0x00007f76ee345fa8: <offset 0x3b9fa8> in /lib/x86_64-linux-gnu/libc.so.6 at 0x00007f76edf8c000
R11=0x00007f76edfc7ca0: __cxa_finalize+0 in /lib/x86_64-linux-gnu/libc.so.6 at 0x00007f76edf8c000
R12=0x0000000000000000 is an unknown value
R13=0x00007f76aeadb932: <offset 0x96932> in /usr/lib/fglrx/libGL.so.1 at 0x00007f76aea45000
R14=0x00007f76cc0008c0 is an unknown value
R15=0x0000000000000000 is an unknown value


Stack: [0x00007f76d6054000,0x00007f76d6155000],  sp=0x00007f76d6153810,  free space=1022k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libX11.so.6+0x33c58]  XQueryExtension+0x28

VM_Operation (0x00007f76eeb7c620): Exit, mode: safepoint, requested by thread 0x00007f76e8009000


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00007f76e8260800 JavaThread "process reaper" daemon [_thread_blocked, id=5971, stack(0x00007f76e406f000,0x00007f76e4097000)]
  0x00007f76e8247800 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=5969, stack(0x00007f76af4c8000,0x00007f76af5c9000)]
  0x00007f76e8214800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=5968, stack(0x00007f76d40c1000,0x00007f76d41c2000)]
  0x00007f76e80ef800 JavaThread "Service Thread" daemon [_thread_blocked, id=5966, stack(0x00007f76d534e000,0x00007f76d544f000)]
  0x00007f76e80ed000 JavaThread "C2 CompilerThread1" daemon [_thread_blocked, id=5965, stack(0x00007f76d544f000,0x00007f76d5550000)]
  0x00007f76e80ea800 JavaThread "C2 CompilerThread0" daemon [_thread_blocked, id=5964, stack(0x00007f76d5550000,0x00007f76d5651000)]
  0x00007f76e809b800 JavaThread "Finalizer" daemon [_thread_blocked, id=5962, stack(0x00007f76d5e52000,0x00007f76d5f53000)]
  0x00007f76e8099000 JavaThread "Reference Handler" daemon [_thread_blocked, id=5961, stack(0x00007f76d5f53000,0x00007f76d6054000)]
  0x00007f76e8009000 JavaThread "main" [_thread_blocked, id=5955, stack(0x00007f76eea7d000,0x00007f76eeb7e000)]

Other Threads:
=>0x00007f76e8091800 VMThread [stack: 0x00007f76d6054000,0x00007f76d6155000] [id=5960]

VM state:at safepoint (shutting down)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x00007f76e80052c0] Threads_lock - owner thread: 0x00007f76e8091800

Heap
 PSYoungGen      total 20288K, used 6169K [0x00000000d7200000, 0x00000000d8830000, 0x0000000100000000)
  eden space 20160K, 30% used [0x00000000d7200000,0x00000000d77ee560,0x00000000d85b0000)
  from space 128K, 75% used [0x00000000d8610000,0x00000000d8628000,0x00000000d8630000)
  to   space 1280K, 0% used [0x00000000d86f0000,0x00000000d86f0000,0x00000000d8830000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7802K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b9eab0,0x00000000818c0000)

Card table byte_map: [0x00007f76e49e6000,0x00007f76e4de5000] byte_map_base: 0x00007f76e45e4000

Polling page: 0x00007f76eeb9f000

Code Cache  [0x00007f76e4de5000, 0x00007f76e5055000, 0x00007f76e7de5000)
 total_blobs=601 nmethods=130 adapters=424 free_code_cache=48397Kb largest_free_block=49535744

Compilation events (10 events):
Event: 18,575 Thread 0x00007f76e80ea800  124             java.util.HashMap$HashIterator::<init> (63 bytes)
Event: 18,585 Thread 0x00007f76e80ea800 nmethod 124 0x00007f76e4e88d50 code [0x00007f76e4e88ea0, 0x00007f76e4e89038]
Event: 19,338 Thread 0x00007f76e80ed000  125   !         org.lwjgl.opengl.LinuxDisplay::lockAWT (30 bytes)
Event: 19,338 Thread 0x00007f76e80ea800  127   !         org.lwjgl.opengl.LinuxDisplay::unlockAWT (30 bytes)
Event: 19,339 Thread 0x00007f76e80ea800 nmethod 127 0x00007f76e4ea3350 code [0x00007f76e4ea34a0, 0x00007f76e4ea3528]
Event: 19,339 Thread 0x00007f76e80ed000 nmethod 125 0x00007f76e4ea1510 code [0x00007f76e4ea1660, 0x00007f76e4ea16e8]
Event: 31,641 Thread 0x00007f76e80ed000  129             java.util.ArrayList$Itr::<init> (6 bytes)
Event: 31,642 Thread 0x00007f76e80ea800  130             java.util.ArrayList$Itr::<init> (26 bytes)
Event: 31,643 Thread 0x00007f76e80ed000 nmethod 129 0x00007f76e4ea1210 code [0x00007f76e4ea1340, 0x00007f76e4ea13d8]
Event: 31,643 Thread 0x00007f76e80ea800 nmethod 130 0x00007f76e4ea2a10 code [0x00007f76e4ea2b40, 0x00007f76e4ea2bd8]

GC Heap History (10 events):
Event: 27,204 GC heap before
{Heap before GC invocations=21 (full 0):
 PSYoungGen      total 23296K, used 22208K [0x00000000d7200000, 0x00000000d8ae0000, 0x0000000100000000)
  eden space 22144K, 100% used [0x00000000d7200000,0x00000000d87a0000,0x00000000d87a0000)
  from space 1152K, 5% used [0x00000000d89c0000,0x00000000d89d0000,0x00000000d8ae0000)
  to   space 1664K, 0% used [0x00000000d87a0000,0x00000000d87a0000,0x00000000d8940000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7d908,0x00000000818c0000)
Event: 27,206 GC heap after
Heap after GC invocations=21 (full 0):
 PSYoungGen      total 21760K, used 64K [0x00000000d7200000, 0x00000000d8a50000, 0x0000000100000000)
  eden space 21696K, 0% used [0x00000000d7200000,0x00000000d7200000,0x00000000d8730000)
  from space 64K, 100% used [0x00000000d87a0000,0x00000000d87b0000,0x00000000d87b0000)
  to   space 1600K, 0% used [0x00000000d88c0000,0x00000000d88c0000,0x00000000d8a50000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7d908,0x00000000818c0000)
}
Event: 28,304 GC heap before
{Heap before GC invocations=22 (full 0):
 PSYoungGen      total 21760K, used 21760K [0x00000000d7200000, 0x00000000d8a50000, 0x0000000100000000)
  eden space 21696K, 100% used [0x00000000d7200000,0x00000000d8730000,0x00000000d8730000)
  from space 64K, 100% used [0x00000000d87a0000,0x00000000d87b0000,0x00000000d87b0000)
  to   space 1600K, 0% used [0x00000000d88c0000,0x00000000d88c0000,0x00000000d8a50000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dab8,0x00000000818c0000)
Event: 28,305 GC heap after
Heap after GC invocations=22 (full 0):
 PSYoungGen      total 22272K, used 64K [0x00000000d7200000, 0x00000000d89b0000, 0x0000000100000000)
  eden space 21312K, 0% used [0x00000000d7200000,0x00000000d7200000,0x00000000d86d0000)
  from space 960K, 6% used [0x00000000d88c0000,0x00000000d88d0000,0x00000000d89b0000)
  to   space 1472K, 0% used [0x00000000d86d0000,0x00000000d86d0000,0x00000000d8840000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dab8,0x00000000818c0000)
}
Event: 29,467 GC heap before
{Heap before GC invocations=23 (full 0):
 PSYoungGen      total 22272K, used 21376K [0x00000000d7200000, 0x00000000d89b0000, 0x0000000100000000)
  eden space 21312K, 100% used [0x00000000d7200000,0x00000000d86d0000,0x00000000d86d0000)
  from space 960K, 6% used [0x00000000d88c0000,0x00000000d88d0000,0x00000000d89b0000)
  to   space 1472K, 0% used [0x00000000d86d0000,0x00000000d86d0000,0x00000000d8840000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dab8,0x00000000818c0000)
Event: 29,468 GC heap after
Heap after GC invocations=23 (full 0):
 PSYoungGen      total 20992K, used 32K [0x00000000d7200000, 0x00000000d8930000, 0x0000000100000000)
  eden space 20928K, 0% used [0x00000000d7200000,0x00000000d7200000,0x00000000d8670000)
  from space 64K, 50% used [0x00000000d86d0000,0x00000000d86d8000,0x00000000d86e0000)
  to   space 1408K, 0% used [0x00000000d87d0000,0x00000000d87d0000,0x00000000d8930000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dab8,0x00000000818c0000)
}
Event: 30,604 GC heap before
{Heap before GC invocations=24 (full 0):
 PSYoungGen      total 20992K, used 20960K [0x00000000d7200000, 0x00000000d8930000, 0x0000000100000000)
  eden space 20928K, 100% used [0x00000000d7200000,0x00000000d8670000,0x00000000d8670000)
  from space 64K, 50% used [0x00000000d86d0000,0x00000000d86d8000,0x00000000d86e0000)
  to   space 1408K, 0% used [0x00000000d87d0000,0x00000000d87d0000,0x00000000d8930000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dbc8,0x00000000818c0000)
Event: 30,605 GC heap after
Heap after GC invocations=24 (full 0):
 PSYoungGen      total 21440K, used 32K [0x00000000d7200000, 0x00000000d88b0000, 0x0000000100000000)
  eden space 20544K, 0% used [0x00000000d7200000,0x00000000d7200000,0x00000000d8610000)
  from space 896K, 3% used [0x00000000d87d0000,0x00000000d87d8000,0x00000000d88b0000)
  to   space 1344K, 0% used [0x00000000d8610000,0x00000000d8610000,0x00000000d8760000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7670K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7dbc8,0x00000000818c0000)
}
Event: 31,730 GC heap before
{Heap before GC invocations=25 (full 0):
 PSYoungGen      total 21440K, used 20576K [0x00000000d7200000, 0x00000000d88b0000, 0x0000000100000000)
  eden space 20544K, 100% used [0x00000000d7200000,0x00000000d8610000,0x00000000d8610000)
  from space 896K, 3% used [0x00000000d87d0000,0x00000000d87d8000,0x00000000d88b0000)
  to   space 1344K, 0% used [0x00000000d8610000,0x00000000d8610000,0x00000000d8760000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7671K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7def8,0x00000000818c0000)
Event: 31,730 GC heap after
Heap after GC invocations=25 (full 0):
 PSYoungGen      total 20288K, used 96K [0x00000000d7200000, 0x00000000d8830000, 0x0000000100000000)
  eden space 20160K, 0% used [0x00000000d7200000,0x00000000d7200000,0x00000000d85b0000)
  from space 128K, 75% used [0x00000000d8610000,0x00000000d8628000,0x00000000d8630000)
  to   space 1280K, 0% used [0x00000000d86f0000,0x00000000d86f0000,0x00000000d8830000)
 ParOldGen       total 83712K, used 1154K [0x0000000085600000, 0x000000008a7c0000, 0x00000000d7200000)
  object space 83712K, 1% used [0x0000000085600000,0x0000000085720b08,0x000000008a7c0000)
 PSPermGen       total 21248K, used 7671K [0x0000000080400000, 0x00000000818c0000, 0x0000000085600000)
  object space 21248K, 36% used [0x0000000080400000,0x0000000080b7def8,0x00000000818c0000)
}

Deoptimization events (4 events):
Event: 1,262 Thread 0x00007f76e8009000 Uncommon trap 87 fr.pc 0x00007f76e4e72600
Event: 5,887 Thread 0x00007f76e8009000 Uncommon trap 199 fr.pc 0x00007f76e4e85b70
Event: 32,048 Thread 0x00007f76e8009000 Uncommon trap -83 fr.pc 0x00007f76e4ea2f28
Event: 32,048 Thread 0x00007f76e8009000 Uncommon trap -83 fr.pc 0x00007f76e4e8a054

Internal exceptions (10 events):
Event: 32,048 Thread 0x00007f76e8009000 Implicit null exception at 0x00007f76e4ea2e38 to 0x00007f76e4ea2f15
Event: 32,048 Thread 0x00007f76e8009000 Implicit null exception at 0x00007f76e4e89f49 to 0x00007f76e4e8a041
Event: 32,048 Thread 0x00007f76e8009000 Threw 0x00000000d76fb030 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,065 Thread 0x00007f76e8009000 Threw 0x00000000d76fedb8 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,125 Thread 0x00007f76e8009000 Threw 0x00000000d770e290 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,128 Thread 0x00007f76e8009000 Threw 0x00000000d7713600 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,131 Thread 0x00007f76e8009000 Threw 0x00000000d771e2b0 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,133 Thread 0x00007f76e8009000 Threw 0x00000000d7722ff8 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,135 Thread 0x00007f76e8009000 Threw 0x00000000d7729330 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166
Event: 32,136 Thread 0x00007f76e8009000 Threw 0x00000000d772e180 at /HUDSON/workspace/jdk7u7-2-build-linux-amd64-product/jdk7u7/hotspot/src/share/vm/prims/jvm.cpp:1166

Events (10 events):
Event: 32,138 Thread 0x00007f76e8869000 Thread added: 0x00007f76e8869000
Event: 32,138 loading class 0x00007f76e81b4920
Event: 32,138 loading class 0x00007f7694000ee0
Event: 32,138 loading class 0x00007f7694000ee0 done
Event: 32,138 loading class 0x00007f7694001080
Event: 32,138 loading class 0x00007f7694001080 done
Event: 32,138 loading class 0x00007f76e81b4920 done
Event: 32,140 Thread 0x00007f76e8869000 Thread exited: 0x00007f76e8869000
Event: 32,140 Thread 0x00007f76e80e8000 Thread exited: 0x00007f76e80e8000
Event: 32,140 Executing VM operation: Exit


Dynamic libraries:
00400000-00401000 r-xp 00000000 08:01 656043                             /usr/lib/jvm/jdk1.7.0_07/bin/java
00600000-00601000 rw-p 00000000 08:01 656043                             /usr/lib/jvm/jdk1.7.0_07/bin/java
0221e000-0223f000 rw-p 00000000 00:00 0                                  [heap]
80400000-818c0000 rw-p 00000000 00:00 0 
818c0000-85600000 rw-p 00000000 00:00 0 
85600000-8a7c0000 rw-p 00000000 00:00 0 
8a7c0000-d7200000 rw-p 00000000 00:00 0 
d7200000-d8830000 rw-p 00000000 00:00 0 
d8830000-d9ad0000 ---p 00000000 00:00 0 
d9ad0000-100000000 rw-p 00000000 00:00 0 
7f7694000000-7f7694021000 rw-p 00000000 00:00 0 
7f7694021000-7f7698000000 ---p 00000000 00:00 0 
7f769b4fc000-7f769b4ff000 ---p 00000000 00:00 0 
7f769b4ff000-7f769b5fd000 rw-p 00000000 00:00 0 
7f769b5fd000-7f769bcfd000 rw-s 0361f000 00:05 10044                      /dev/ati/card0
7f769bcfd000-7f769bdfd000 rw-p 00000000 00:00 0 
7f769bdfd000-7f769bdff000 r-xp 00000000 08:01 12327915                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f769bdff000-7f769bffe000 ---p 00002000 08:01 12327915                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f769bffe000-7f769bfff000 r--p 00001000 08:01 12327915                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f769bfff000-7f769c000000 rw-p 00002000 08:01 12327915                   /usr/lib/x86_64-linux-gnu/libXinerama.so.1.0.0
7f769c000000-7f769c021000 rw-p 00000000 00:00 0 
7f769c021000-7f76a0000000 ---p 00000000 00:00 0 
7f76a0000000-7f76a0021000 rw-p 00000000 00:00 0 
7f76a0021000-7f76a4000000 ---p 00000000 00:00 0 
7f76a4000000-7f76a4021000 rw-p 00000000 00:00 0 
7f76a4021000-7f76a8000000 ---p 00000000 00:00 0 
7f76a8000000-7f76a8021000 rw-p 00000000 00:00 0 
7f76a8021000-7f76ac000000 ---p 00000000 00:00 0 
7f76ac02a000-7f76ac0f2000 rw-p 00000000 00:00 0 
7f76ac0f2000-7f76ac12d000 r-xp 00000000 08:01 12322472                   /usr/lib/fglrx/libatiadlxx.so
7f76ac12d000-7f76ac22d000 ---p 0003b000 08:01 12322472                   /usr/lib/fglrx/libatiadlxx.so
7f76ac22d000-7f76ac236000 rw-p 0003b000 08:01 12322472                   /usr/lib/fglrx/libatiadlxx.so
7f76ac236000-7f76ac247000 rw-p 00000000 00:00 0 
7f76ac247000-7f76ac24e000 r-xp 00000000 08:01 12322502                   /usr/lib/fglrx/libatiuki.so.1.0
7f76ac24e000-7f76ac34e000 ---p 00007000 08:01 12322502                   /usr/lib/fglrx/libatiuki.so.1.0
7f76ac34e000-7f76ac34f000 rw-p 00007000 08:01 12322502                   /usr/lib/fglrx/libatiuki.so.1.0
7f76ac34f000-7f76ac350000 rw-p 00000000 00:00 0 
7f76ac350000-7f76ae2aa000 r-xp 00000000 08:01 12849102                   /usr/lib/fglrx/dri/fglrx_dri.so
7f76ae2aa000-7f76ae3aa000 ---p 01f5a000 08:01 12849102                   /usr/lib/fglrx/dri/fglrx_dri.so
7f76ae3aa000-7f76ae4f8000 rwxp 01f5a000 08:01 12849102                   /usr/lib/fglrx/dri/fglrx_dri.so
7f76ae4f8000-7f76ae61e000 rwxp 00000000 00:00 0 
7f76ae61e000-7f76ae633000 r-xp 00000000 08:01 655882                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnet.so
7f76ae633000-7f76ae833000 ---p 00015000 08:01 655882                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnet.so
7f76ae833000-7f76ae834000 rw-p 00015000 08:01 655882                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnet.so
7f76ae834000-7f76ae844000 r-xp 00000000 08:01 655879                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnio.so
7f76ae844000-7f76aea44000 ---p 00010000 08:01 655879                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnio.so
7f76aea44000-7f76aea45000 rw-p 00010000 08:01 655879                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libnio.so
7f76aea45000-7f76aeb08000 r-xp 00000000 08:01 12322474                   /usr/lib/fglrx/libGL.so.1.2
7f76aeb08000-7f76aec07000 ---p 000c3000 08:01 12322474                   /usr/lib/fglrx/libGL.so.1.2
7f76aec07000-7f76aec2e000 rwxp 000c2000 08:01 12322474                   /usr/lib/fglrx/libGL.so.1.2
7f76aec2e000-7f76aec4e000 rwxp 00000000 00:00 0 
7f76aec4e000-7f76aec52000 r-xp 00000000 08:01 12327935                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f76aec52000-7f76aee51000 ---p 00004000 08:01 12327935                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f76aee51000-7f76aee52000 r--p 00003000 08:01 12327935                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f76aee52000-7f76aee53000 rw-p 00004000 08:01 12327935                   /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f76aee53000-7f76aee5b000 r-xp 00000000 08:01 12327925                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f76aee5b000-7f76af05a000 ---p 00008000 08:01 12327925                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f76af05a000-7f76af05b000 r--p 00007000 08:01 12327925                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f76af05b000-7f76af05c000 rw-p 00008000 08:01 12327925                   /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f76af05c000-7f76af0c4000 r-xp 00000000 08:05 25561027                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/native/linux/liblwjgl64.so
7f76af0c4000-7f76af2c4000 ---p 00068000 08:05 25561027                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/native/linux/liblwjgl64.so
7f76af2c4000-7f76af2c6000 r--p 00068000 08:05 25561027                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/native/linux/liblwjgl64.so
7f76af2c6000-7f76af2c7000 rw-p 0006a000 08:05 25561027                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/native/linux/liblwjgl64.so
7f76af2c7000-7f76af2c8000 r-xp 00000000 08:01 655922                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjawt.so
7f76af2c8000-7f76af4c7000 ---p 00001000 08:01 655922                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjawt.so
7f76af4c7000-7f76af4c8000 rw-p 00000000 08:01 655922                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjawt.so
7f76af4c8000-7f76af4cb000 ---p 00000000 00:00 0 
7f76af4cb000-7f76af5c9000 rw-p 00000000 00:00 0 
7f76af5c9000-7f76af5ce000 r-xp 00000000 08:01 12327909                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f76af5ce000-7f76af7cd000 ---p 00005000 08:01 12327909                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f76af7cd000-7f76af7ce000 r--p 00004000 08:01 12327909                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f76af7ce000-7f76af7cf000 rw-p 00005000 08:01 12327909                   /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f76af7cf000-7f76af7d8000 r-xp 00000000 08:01 12327901                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f76af7d8000-7f76af9d7000 ---p 00009000 08:01 12327901                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f76af9d7000-7f76af9d8000 r--p 00008000 08:01 12327901                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f76af9d8000-7f76af9d9000 rw-p 00009000 08:01 12327901                   /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f76af9d9000-7f76af9de000 r-xp 00000000 08:01 12327905                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f76af9de000-7f76afbdd000 ---p 00005000 08:01 12327905                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f76afbdd000-7f76afbde000 r--p 00004000 08:01 12327905                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f76afbde000-7f76afbdf000 rw-p 00005000 08:01 12327905                   /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f76afbdf000-7f76afbe1000 r-xp 00000000 08:01 12327894                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f76afbe1000-7f76afde0000 ---p 00002000 08:01 12327894                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f76afde0000-7f76afde1000 r--p 00001000 08:01 12327894                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f76afde1000-7f76afde2000 rw-p 00002000 08:01 12327894                   /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f76afde2000-7f76afdff000 r-xp 00000000 08:01 12328493                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f76afdff000-7f76afffe000 ---p 0001d000 08:01 12328493                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f76afffe000-7f76affff000 r--p 0001c000 08:01 12328493                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f76affff000-7f76b0000000 rw-p 0001d000 08:01 12328493                   /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f76b0000000-7f76b0512000 rw-p 00000000 00:00 0 
7f76b0512000-7f76b4000000 ---p 00000000 00:00 0 
7f76b4000000-7f76b4021000 rw-p 00000000 00:00 0 
7f76b4021000-7f76b8000000 ---p 00000000 00:00 0 
7f76b8000000-7f76b8021000 rw-p 00000000 00:00 0 
7f76b8021000-7f76bc000000 ---p 00000000 00:00 0 
7f76bc000000-7f76bc369000 rw-p 00000000 00:00 0 
7f76bc369000-7f76c0000000 ---p 00000000 00:00 0 
7f76c0000000-7f76c0021000 rw-p 00000000 00:00 0 
7f76c0021000-7f76c4000000 ---p 00000000 00:00 0 
7f76c4000000-7f76c4021000 rw-p 00000000 00:00 0 
7f76c4021000-7f76c8000000 ---p 00000000 00:00 0 
7f76c8000000-7f76c8021000 rw-p 00000000 00:00 0 
7f76c8021000-7f76cc000000 ---p 00000000 00:00 0 
7f76cc000000-7f76cc021000 rw-p 00000000 00:00 0 
7f76cc021000-7f76d0000000 ---p 00000000 00:00 0 
7f76d0000000-7f76d0021000 rw-p 00000000 00:00 0 
7f76d0021000-7f76d4000000 ---p 00000000 00:00 0 
7f76d4041000-7f76d40c1000 rw-p 00000000 00:00 0 
7f76d40c1000-7f76d40c4000 ---p 00000000 00:00 0 
7f76d40c4000-7f76d41c2000 rw-p 00000000 00:00 0 
7f76d41c2000-7f76d41d0000 r-xp 00000000 08:01 12327913                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f76d41d0000-7f76d43cf000 ---p 0000e000 08:01 12327913                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f76d43cf000-7f76d43d0000 r--p 0000d000 08:01 12327913                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f76d43d0000-7f76d43d1000 rw-p 0000e000 08:01 12327913                   /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f76d43d1000-7f76d43d6000 r-xp 00000000 08:01 12327931                   /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f76d43d6000-7f76d45d5000 ---p 00005000 08:01 12327931                   /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f76d45d5000-7f76d45d6000 r--p 00004000 08:01 12327931                   /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f76d45d6000-7f76d45d7000 rw-p 00005000 08:01 12327931                   /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f76d45d7000-7f76d45e0000 r-xp 00000000 08:01 12327927                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f76d45e0000-7f76d47df000 ---p 00009000 08:01 12327927                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f76d47df000-7f76d47e0000 r--p 00008000 08:01 12327927                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f76d47e0000-7f76d47e1000 rw-p 00009000 08:01 12327927                   /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f76d47e1000-7f76d4910000 r-xp 00000000 08:01 12327892                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f76d4910000-7f76d4b10000 ---p 0012f000 08:01 12327892                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f76d4b10000-7f76d4b11000 r--p 0012f000 08:01 12327892                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f76d4b11000-7f76d4b15000 rw-p 00130000 08:01 12327892                   /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f76d4b15000-7f76d4b25000 r-xp 00000000 08:01 12327907                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f76d4b25000-7f76d4d24000 ---p 00010000 08:01 12327907                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f76d4d24000-7f76d4d25000 r--p 0000f000 08:01 12327907                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f76d4d25000-7f76d4d26000 rw-p 00010000 08:01 12327907                   /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f76d4d26000-7f76d4d76000 r-xp 00000000 08:01 655900                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/xawt/libmawt.so
7f76d4d76000-7f76d4f76000 ---p 00050000 08:01 655900                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/xawt/libmawt.so
7f76d4f76000-7f76d4f7a000 rw-p 00050000 08:01 655900                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/xawt/libmawt.so
7f76d4f7a000-7f76d4f7b000 rw-p 00000000 00:00 0 
7f76d4f7b000-7f76d501d000 r-xp 00000000 08:01 655916                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libawt.so
7f76d501d000-7f76d521d000 ---p 000a2000 08:01 655916                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libawt.so
7f76d521d000-7f76d5229000 rw-p 000a2000 08:01 655916                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libawt.so
7f76d5229000-7f76d524d000 rw-p 00000000 00:00 0 
7f76d524d000-7f76d524e000 ---p 00000000 00:00 0 
7f76d524e000-7f76d534e000 rw-p 00000000 00:00 0 
7f76d534e000-7f76d5351000 ---p 00000000 00:00 0 
7f76d5351000-7f76d544f000 rw-p 00000000 00:00 0 
7f76d544f000-7f76d5452000 ---p 00000000 00:00 0 
7f76d5452000-7f76d5550000 rw-p 00000000 00:00 0 
7f76d5550000-7f76d5553000 ---p 00000000 00:00 0 
7f76d5553000-7f76d5651000 rw-p 00000000 00:00 0 
7f76d5651000-7f76d5654000 ---p 00000000 00:00 0 
7f76d5654000-7f76d5752000 rw-p 00000000 00:00 0 
7f76d5752000-7f76d5e52000 r--p 00000000 08:01 12327231                   /usr/lib/locale/locale-archive
7f76d5e52000-7f76d5e55000 ---p 00000000 00:00 0 
7f76d5e55000-7f76d5f53000 rw-p 00000000 00:00 0 
7f76d5f53000-7f76d5f56000 ---p 00000000 00:00 0 
7f76d5f56000-7f76d6054000 rw-p 00000000 00:00 0 
7f76d6054000-7f76d6055000 ---p 00000000 00:00 0 
7f76d6055000-7f76d8000000 rw-p 00000000 00:00 0 
7f76d8000000-7f76d8021000 rw-p 00000000 00:00 0 
7f76d8021000-7f76dc000000 ---p 00000000 00:00 0 
7f76dc020000-7f76e0000000 rw-p 00000000 00:00 0 
7f76e0000000-7f76e0021000 rw-p 00000000 00:00 0 
7f76e0021000-7f76e4000000 ---p 00000000 00:00 0 
7f76e401e000-7f76e403e000 rw-s c0700000 00:05 10044                      /dev/ati/card0
7f76e403e000-7f76e406f000 rw-p 00000000 00:00 0 
7f76e406f000-7f76e4072000 ---p 00000000 00:00 0 
7f76e4072000-7f76e4198000 rw-p 00000000 00:00 0 
7f76e4198000-7f76e4354000 r--s 039d3000 08:01 527778                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/rt.jar
7f76e4354000-7f76e4355000 ---p 00000000 00:00 0 
7f76e4355000-7f76e4455000 rw-p 00000000 00:00 0 
7f76e4455000-7f76e4456000 ---p 00000000 00:00 0 
7f76e4456000-7f76e4556000 rw-p 00000000 00:00 0 
7f76e4556000-7f76e4557000 ---p 00000000 00:00 0 
7f76e4557000-7f76e4657000 rw-p 00000000 00:00 0 
7f76e4657000-7f76e4658000 ---p 00000000 00:00 0 
7f76e4658000-7f76e4781000 rw-p 00000000 00:00 0 
7f76e4781000-7f76e49e6000 rw-p 00000000 00:00 0 
7f76e49e6000-7f76e49f1000 rw-p 00000000 00:00 0 
7f76e49f1000-7f76e4a0f000 rw-p 00000000 00:00 0 
7f76e4a0f000-7f76e4a38000 rw-p 00000000 00:00 0 
7f76e4a38000-7f76e4c9d000 rw-p 00000000 00:00 0 
7f76e4c9d000-7f76e4ca9000 rw-p 00000000 00:00 0 
7f76e4ca9000-7f76e4cb2000 ---p 00000000 00:00 0 
7f76e4cb2000-7f76e4de4000 rw-p 00000000 00:00 0 
7f76e4de4000-7f76e4de5000 rw-p 00000000 00:00 0 
7f76e4de5000-7f76e5055000 rwxp 00000000 00:00 0 
7f76e5055000-7f76e7de5000 rw-p 00000000 00:00 0 
7f76e7de5000-7f76e7dff000 r-xp 00000000 08:01 655888                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libzip.so
7f76e7dff000-7f76e7fff000 ---p 0001a000 08:01 655888                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libzip.so
7f76e7fff000-7f76e8000000 rw-p 0001a000 08:01 655888                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libzip.so
7f76e8000000-7f76e8c3f000 rw-p 00000000 00:00 0 
7f76e8c3f000-7f76ec000000 ---p 00000000 00:00 0 
7f76ec004000-7f76ec00b000 r--s 00000000 08:01 12584908                   /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f76ec00b000-7f76ec02f000 r--p 00000000 08:01 13242243                   /usr/share/locale-langpack/cs/LC_MESSAGES/libc.mo
7f76ec02f000-7f76ec0d2000 rw-p 00000000 00:00 0 
7f76ec0d2000-7f76ec0f0000 rw-p 00000000 00:00 0 
7f76ec0f0000-7f76ec0fc000 r-xp 00000000 08:01 12848695                   /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f76ec0fc000-7f76ec2fb000 ---p 0000c000 08:01 12848695                   /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f76ec2fb000-7f76ec2fc000 r--p 0000b000 08:01 12848695                   /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f76ec2fc000-7f76ec2fd000 rw-p 0000c000 08:01 12848695                   /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f76ec2fd000-7f76ec307000 r-xp 00000000 08:01 12848699                   /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f76ec307000-7f76ec507000 ---p 0000a000 08:01 12848699                   /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f76ec507000-7f76ec508000 r--p 0000a000 08:01 12848699                   /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f76ec508000-7f76ec509000 rw-p 0000b000 08:01 12848699                   /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f76ec509000-7f76ec520000 r-xp 00000000 08:01 12848689                   /lib/x86_64-linux-gnu/libnsl-2.15.so
7f76ec520000-7f76ec71f000 ---p 00017000 08:01 12848689                   /lib/x86_64-linux-gnu/libnsl-2.15.so
7f76ec71f000-7f76ec720000 r--p 00016000 08:01 12848689                   /lib/x86_64-linux-gnu/libnsl-2.15.so
7f76ec720000-7f76ec721000 rw-p 00017000 08:01 12848689                   /lib/x86_64-linux-gnu/libnsl-2.15.so
7f76ec721000-7f76ec723000 rw-p 00000000 00:00 0 
7f76ec723000-7f76ec72b000 r-xp 00000000 08:01 12848691                   /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f76ec72b000-7f76ec92a000 ---p 00008000 08:01 12848691                   /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f76ec92a000-7f76ec92b000 r--p 00007000 08:01 12848691                   /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f76ec92b000-7f76ec92c000 rw-p 00008000 08:01 12848691                   /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f76ec92c000-7f76ec955000 r-xp 00000000 08:01 655918                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjava.so
7f76ec955000-7f76ecb55000 ---p 00029000 08:01 655918                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjava.so
7f76ecb55000-7f76ecb57000 rw-p 00029000 08:01 655918                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libjava.so
7f76ecb57000-7f76ecb64000 r-xp 00000000 08:01 655868                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libverify.so
7f76ecb64000-7f76ecd63000 ---p 0000d000 08:01 655868                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libverify.so
7f76ecd63000-7f76ecd65000 rw-p 0000c000 08:01 655868                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/libverify.so
7f76ecd65000-7f76ecd6c000 r-xp 00000000 08:01 12848730                   /lib/x86_64-linux-gnu/librt-2.15.so
7f76ecd6c000-7f76ecf6b000 ---p 00007000 08:01 12848730                   /lib/x86_64-linux-gnu/librt-2.15.so
7f76ecf6b000-7f76ecf6c000 r--p 00006000 08:01 12848730                   /lib/x86_64-linux-gnu/librt-2.15.so
7f76ecf6c000-7f76ecf6d000 rw-p 00007000 08:01 12848730                   /lib/x86_64-linux-gnu/librt-2.15.so
7f76ecf6d000-7f76ed066000 r-xp 00000000 08:01 12848676                   /lib/x86_64-linux-gnu/libm-2.15.so
7f76ed066000-7f76ed265000 ---p 000f9000 08:01 12848676                   /lib/x86_64-linux-gnu/libm-2.15.so
7f76ed265000-7f76ed266000 r--p 000f8000 08:01 12848676                   /lib/x86_64-linux-gnu/libm-2.15.so
7f76ed266000-7f76ed267000 rw-p 000f9000 08:01 12848676                   /lib/x86_64-linux-gnu/libm-2.15.so
7f76ed267000-7f76edcae000 r-xp 00000000 08:01 655909                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/server/libjvm.so
7f76edcae000-7f76edead000 ---p 00a47000 08:01 655909                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/server/libjvm.so
7f76edead000-7f76edf50000 rw-p 00a46000 08:01 655909                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/server/libjvm.so
7f76edf50000-7f76edf8c000 rw-p 00000000 00:00 0 
7f76edf8c000-7f76ee13f000 r-xp 00000000 08:01 12848644                   /lib/x86_64-linux-gnu/libc-2.15.so
7f76ee13f000-7f76ee33e000 ---p 001b3000 08:01 12848644                   /lib/x86_64-linux-gnu/libc-2.15.so
7f76ee33e000-7f76ee342000 r--p 001b2000 08:01 12848644                   /lib/x86_64-linux-gnu/libc-2.15.so
7f76ee342000-7f76ee344000 rw-p 001b6000 08:01 12848644                   /lib/x86_64-linux-gnu/libc-2.15.so
7f76ee344000-7f76ee349000 rw-p 00000000 00:00 0 
7f76ee349000-7f76ee34b000 r-xp 00000000 08:01 12848657                   /lib/x86_64-linux-gnu/libdl-2.15.so
7f76ee34b000-7f76ee54b000 ---p 00002000 08:01 12848657                   /lib/x86_64-linux-gnu/libdl-2.15.so
7f76ee54b000-7f76ee54c000 r--p 00002000 08:01 12848657                   /lib/x86_64-linux-gnu/libdl-2.15.so
7f76ee54c000-7f76ee54d000 rw-p 00003000 08:01 12848657                   /lib/x86_64-linux-gnu/libdl-2.15.so
7f76ee54d000-7f76ee563000 r-xp 00000000 08:01 655877                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/jli/libjli.so
7f76ee563000-7f76ee762000 ---p 00016000 08:01 655877                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/jli/libjli.so
7f76ee762000-7f76ee763000 rw-p 00015000 08:01 655877                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/amd64/jli/libjli.so
7f76ee763000-7f76ee77b000 r-xp 00000000 08:01 12848724                   /lib/x86_64-linux-gnu/libpthread-2.15.so
7f76ee77b000-7f76ee97a000 ---p 00018000 08:01 12848724                   /lib/x86_64-linux-gnu/libpthread-2.15.so
7f76ee97a000-7f76ee97b000 r--p 00017000 08:01 12848724                   /lib/x86_64-linux-gnu/libpthread-2.15.so
7f76ee97b000-7f76ee97c000 rw-p 00018000 08:01 12848724                   /lib/x86_64-linux-gnu/libpthread-2.15.so
7f76ee97c000-7f76ee980000 rw-p 00000000 00:00 0 
7f76ee980000-7f76ee9a2000 r-xp 00000000 08:01 12848624                   /lib/x86_64-linux-gnu/ld-2.15.so
7f76ee9a6000-7f76ee9b0000 r--s 00371000 08:01 527772                     /usr/lib/jvm/jdk1.7.0_07/jre/lib/charsets.jar
7f76ee9b0000-7f76ee9bd000 r--s 000d9000 08:05 25561020                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/lwjgl.jar
7f76ee9bd000-7f76ee9c7000 rw-p 00000000 00:00 0 
7f76ee9c7000-7f76eea7d000 rw-p 00000000 00:00 0 
7f76eea7d000-7f76eea80000 ---p 00000000 00:00 0 
7f76eea80000-7f76eeb82000 rw-p 00000000 00:00 0 
7f76eeb88000-7f76eeb89000 rw-s 0361e000 00:05 10044                      /dev/ati/card0
7f76eeb89000-7f76eeb8b000 rw-s 0361b000 00:05 10044                      /dev/ati/card0
7f76eeb8b000-7f76eeb96000 r--s 00093000 08:05 25561021                   /home/jakub/Dokumenty/Java/Megaman_portal/lib/slick.jar
7f76eeb96000-7f76eeb9e000 rw-s 00000000 08:01 7340072                    /tmp/hsperfdata_jakub/5950 (deleted)
7f76eeb9e000-7f76eeb9f000 rw-p 00000000 00:00 0 
7f76eeb9f000-7f76eeba0000 ---p 00000000 00:00 0 
7f76eeba0000-7f76eeba2000 rw-p 00000000 00:00 0 
7f76eeba2000-7f76eeba3000 r--p 00022000 08:01 12848624                   /lib/x86_64-linux-gnu/ld-2.15.so
7f76eeba3000-7f76eeba5000 rw-p 00023000 08:01 12848624                   /lib/x86_64-linux-gnu/ld-2.15.so
7fffbf649000-7fffbf66a000 rw-p 00000000 00:00 0                          [stack]
7fffbf6a0000-7fffbf6a1000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
jvm_args: -Djava.library.path=/home/jakub/Dokumenty/Java/Megaman_portal/lib/native/linux -Dfile.encoding=UTF-8 
java_command: Program
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
SHELL=/bin/bash
DISPLAY=:0

Signal Handlers:
SIGSEGV: [libjvm.so+0x8a5a80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x8a5a80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x741b60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x741b60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x741b60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x741b60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x7414b0], sa_mask[0]=0x00000004, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x743840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x743840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x743840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x743840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64
libc:glibc 2.15 NPTL 2.15 
rlimit: STACK 8192k, CORE 0k, NPROC 62587, NOFILE 4096, AS infinity
load average:0,60 0,87 0,93

/proc/meminfo:
MemTotal:        8028760 kB
MemFree:         4911208 kB
Buffers:          205740 kB
Cached:          1146496 kB
SwapCached:            0 kB
Active:          1884788 kB
Inactive:         744592 kB
Active(anon):    1277944 kB
Inactive(anon):    19488 kB
Active(file):     606844 kB
Inactive(file):   725104 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:      12572668 kB
SwapFree:       12572668 kB
Dirty:               128 kB
Writeback:             0 kB
AnonPages:       1277164 kB
Mapped:           279812 kB
Shmem:             20296 kB
Slab:             140256 kB
SReclaimable:     109960 kB
SUnreclaim:        30296 kB
KernelStack:        3328 kB
PageTables:        25796 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    16587048 kB
Committed_AS:    3253544 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      586492 kB
VmallocChunk:   34359149016 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      227328 kB
DirectMap2M:     8011776 kB


CPU:total 4 (2 cores per cpu, 2 threads per core) family 6 model 42 stepping 7, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1, sse4.2, popcnt, avx, ht, tsc, tscinvbit

/proc/cpuinfo:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4789.14
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4789.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 2401.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4789.09
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
stepping    : 7
microcode    : 0x1a
cpu MHz        : 800.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 2
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 4789.10
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:



Memory: 4k page, physical 8028760k(4911208k free), swap 12572668k(12572668k free)

vm_info: Java HotSpot(TM) 64-Bit Server VM (23.3-b01) for linux-amd64 JRE (1.7.0_07-b10), built on Aug 28 2012 17:44:05 by "java_re" with gcc 4.3.0 20080428 (Red Hat 4.3.0-8)

time: Sat Sep 29 13:15:28 2012
elapsed time: 32 seconds

```

---

