---
title: "alt+f2 crash"
date: 2015-12-12
forum: New to Ubuntu
---

### Post by cosy2 on 2015-12-12
```
Application: krunner (0.1)
 (Compiled from sources)
Qt Version: 5.4.2
Operating System: Linux 4.2.0-19-generic x86_64
Distribution: Ubuntu 15.10
```

```
-- Backtrace:
Application: krunner (krunner), signal: Segmentation fault
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7f968f30d800 (LWP 1873))]

Thread 35 (Thread 0x7f9679b19700 (LWP 1874)):
#0  0x00007f968bdc98dd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f968b2bbbd2 in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#2  0x00007f968b2bd74f in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#3  0x00007f967c6aea39 in QXcbEventReader::run (this=0xc0f9b0) at qxcbconnection.cpp:1105
#4  0x00007f968c4bc2be in QThreadPrivate::start (arg=0xc0f9b0) at thread/qthread_unix.cpp:337
#5  0x00007f968a0286aa in start_thread (arg=0x7f9679b19700) at pthread_create.c:333
#6  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 34 (Thread 0x7f96700ae700 (LWP 1885)):
#0  0x00007f968bdc549d in read () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f9684938f75 in ?? () from /usr/lib/nvidia-352/tls/libnvidia-tls.so.352.63
#2  0x00007f96894ec4e0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f96894a8cd4 in g_main_context_check () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f96894a9190 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f96894a92fc in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x00007f968c6f329b in QEventDispatcherGlib::processEvents (this=0x7f96680008c0, flags=...) at kernel/qeventdispatcher_glib.cpp:420
#7  0x00007f968c69975a in QEventLoop::exec (this=this@entry=0x7f96700adda0, flags=..., flags@entry=...) at kernel/qeventloop.cpp:204
#8  0x00007f968c4b73d4 in QThread::exec (this=<optimized out>) at thread/qthread.cpp:503
#9  0x00007f968e2bef85 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#10 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x10a6bf0) at thread/qthread_unix.cpp:337
#11 0x00007f968a0286aa in start_thread (arg=0x7f96700ae700) at pthread_create.c:333
#12 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 33 (Thread 0x7f9666cd9700 (LWP 9217)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0xc229a0) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc10d60, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f968e79eb3e in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#4  0x00007f968e79f3c3 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#5  0x00007f968c4bc2be in QThreadPrivate::start (arg=0xc10ce0) at thread/qthread_unix.cpp:337
#6  0x00007f968a0286aa in start_thread (arg=0x7f9666cd9700) at pthread_create.c:333
#7  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 32 (Thread 0x7f965ba35700 (LWP 9218)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x13693e0) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f965ba35700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 31 (Thread 0x7f965b234700 (LWP 9219)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x136eac0) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f965b234700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 30 (Thread 0x7f965aa33700 (LWP 9220)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x1369230) at thread/qthread_unix.cpp:337
#20 0x00007f968a0286aa in start_thread (arg=0x7f965aa33700) at pthread_create.c:333
#21 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 29 (Thread 0x7f965a232700 (LWP 9221)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9654002f90) at thread/qthread_unix.cpp:337
#20 0x00007f968a0286aa in start_thread (arg=0x7f965a232700) at pthread_create.c:333
#21 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 28 (Thread 0x7f9659a31700 (LWP 9222)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x11b5b00) at thread/qthread_unix.cpp:337
#26 0x00007f968a0286aa in start_thread (arg=0x7f9659a31700) at pthread_create.c:333
#27 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 27 (Thread 0x7f9659230700 (LWP 9223)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f964c002f90) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f9659230700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 26 (Thread 0x7f9658a2f700 (LWP 9224)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9650002d90) at thread/qthread_unix.cpp:337
#16 0x00007f968a0286aa in start_thread (arg=0x7f9658a2f700) at pthread_create.c:333
#17 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 25 (Thread 0x7f963bfff700 (LWP 9225)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f963c002d90) at thread/qthread_unix.cpp:337
#12 0x00007f968a0286aa in start_thread (arg=0x7f963bfff700) at pthread_create.c:333
#13 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 24 (Thread 0x7f96337fe700 (LWP 9226)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9644003190) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f96337fe700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 23 (Thread 0x7f963b7fe700 (LWP 9227)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9634002f90) at thread/qthread_unix.cpp:337
#16 0x00007f968a0286aa in start_thread (arg=0x7f963b7fe700) at pthread_create.c:333
#17 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 22 (Thread 0x7f963affd700 (LWP 9228)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9648002d90) at thread/qthread_unix.cpp:337
#16 0x00007f968a0286aa in start_thread (arg=0x7f963affd700) at pthread_create.c:333
#17 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 21 (Thread 0x7f963a7fc700 (LWP 9229)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f964c003650) at thread/qthread_unix.cpp:337
#22 0x00007f968a0286aa in start_thread (arg=0x7f963a7fc700) at pthread_create.c:333
#23 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 20 (Thread 0x7f9639ffb700 (LWP 9230)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9628003190) at thread/qthread_unix.cpp:337
#24 0x00007f968a0286aa in start_thread (arg=0x7f9639ffb700) at pthread_create.c:333
#25 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 19 (Thread 0x7f96397fa700 (LWP 9231)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9650003350) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f96397fa700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 18 (Thread 0x7f9638ff9700 (LWP 9232)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9640003190) at thread/qthread_unix.cpp:337
#28 0x00007f968a0286aa in start_thread (arg=0x7f9638ff9700) at pthread_create.c:333
#29 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 17 (Thread 0x7f9633fff700 (LWP 9233)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#28 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#29 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#30 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#31 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x136e890) at thread/qthread_unix.cpp:337
#32 0x00007f968a0286aa in start_thread (arg=0x7f9633fff700) at pthread_create.c:333
#33 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 16 (Thread 0x7f9632ffd700 (LWP 9234)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#28 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#29 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#30 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#31 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#32 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#33 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f962c0027d0) at thread/qthread_unix.cpp:337
#34 0x00007f968a0286aa in start_thread (arg=0x7f9632ffd700) at pthread_create.c:333
#35 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 15 (Thread 0x7f96327fc700 (LWP 9235)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9634003550) at thread/qthread_unix.cpp:337
#16 0x00007f968a0286aa in start_thread (arg=0x7f96327fc700) at pthread_create.c:333
#17 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 14 (Thread 0x7f9631ffb700 (LWP 9236)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9610003190) at thread/qthread_unix.cpp:337
#18 0x00007f968a0286aa in start_thread (arg=0x7f9631ffb700) at pthread_create.c:333
#19 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 13 (Thread 0x7f96317fa700 (LWP 9237)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#28 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#29 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#30 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#31 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#32 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#33 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#34 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#35 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#36 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#37 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#38 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#39 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#40 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#41 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#42 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#43 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#44 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#45 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#46 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#47 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#48 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#49 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#50 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#51 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#52 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#53 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#54 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#55 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#56 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#57 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#58 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#59 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#60 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#61 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#62 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#63 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#64 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#65 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#66 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#67 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#68 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#69 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#70 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#71 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9604003190) at thread/qthread_unix.cpp:337
#72 0x00007f968a0286aa in start_thread (arg=0x7f96317fa700) at pthread_create.c:333
#73 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 12 (Thread 0x7f9630ff9700 (LWP 9238)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9620002b90) at thread/qthread_unix.cpp:337
#14 0x00007f968a0286aa in start_thread (arg=0x7f9630ff9700) at pthread_create.c:333
#15 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 11 (Thread 0x7f9603fff700 (LWP 9239)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#28 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#29 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#30 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#31 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#32 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#33 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#34 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#35 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#36 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#37 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#38 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#39 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f95fc002d90) at thread/qthread_unix.cpp:337
#40 0x00007f968a0286aa in start_thread (arg=0x7f9603fff700) at pthread_create.c:333
#41 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 10 (Thread 0x7f96037fe700 (LWP 9240)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f968c4bc2be in QThreadPrivate::start (arg=0x7f9618003190) at thread/qthread_unix.cpp:337
#10 0x00007f968a0286aa in start_thread (arg=0x7f96037fe700) at pthread_create.c:333
#11 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 9 (Thread 0x7f9602ffd700 (LWP 9241)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x00007f968c4bd55b in QWaitConditionPrivate::wait (time=18446744073709551615, this=0x1a0ce80) at thread/qwaitcondition_unix.cpp:136
#2  QWaitCondition::wait (this=<optimized out>, mutex=0xc67770, time=18446744073709551615) at thread/qwaitcondition_unix.cpp:208
#3  0x00007f966cb6829f in ThreadWeaver::Weaver::takeFirstAvailableJobOrSuspendOrWait(ThreadWeaver::Thread*, bool, bool, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#4  0x00007f966cb6c4c8 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#5  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#6  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#7  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#8  0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#9  0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#10 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#11 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#12 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#13 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#14 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#15 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#16 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#17 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#18 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#19 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#20 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#21 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#22 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#23 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#24 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#25 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#26 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#27 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#28 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#29 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#30 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#31 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#32 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#33 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#34 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#35 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#36 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#37 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#38 0x00007f966cb6c522 in ?? () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#39 0x00007f966cb6744d in ThreadWeaver::Weaver::applyForWork(ThreadWeaver::Thread*, bool) () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#40 0x00007f966cb6a423 in ThreadWeaver::Thread::run() () from /usr/lib/x86_64-linux-gnu/libKF5ThreadWeaver.so.5
#41 0x00007f968c4bc2be in QThreadPrivate::start (arg=0x136e3a0) at thread/qthread_unix.cpp:337
#42 0x00007f968a0286aa in start_thread (arg=0x7f9602ffd700) at pthread_create.c:333
#43 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 8 (Thread 0x7f95edb8a700 (LWP 28159)):
#0  0x00007f968bdc549d in read () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f9684938f75 in ?? () from /usr/lib/nvidia-352/tls/libnvidia-tls.so.352.63
#2  0x00007f967dfa19c1 in pa_read () from /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-6.0.so
#3  0x00007f967e83f7fe in pa_mainloop_prepare () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#4  0x00007f967e840270 in pa_mainloop_iterate () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#5  0x00007f967e840330 in pa_mainloop_run () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#6  0x00007f967e84e476 in ?? () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#7  0x00007f967dfce4d8 in ?? () from /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-6.0.so
#8  0x00007f968a0286aa in start_thread (arg=0x7f95edb8a700) at pthread_create.c:333
#9  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 7 (Thread 0x7f94a3b9b700 (LWP 28160)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ef075dbd in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#3  0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f968a0286aa in start_thread (arg=0x7f94a3b9b700) at pthread_create.c:333
#6  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 6 (Thread 0x7f94a2d3b700 (LWP 28161)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ef075dbd in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#3  0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f968a0286aa in start_thread (arg=0x7f94a2d3b700) at pthread_create.c:333
#6  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 5 (Thread 0x7f94a253a700 (LWP 28162)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ee4fd2b2 in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#3  0x00007f95ee4fe5d0 in gst_data_queue_pop () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#4  0x00007f95ec268229 in ?? () from /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcoreelements.so
#5  0x00007f95ef075c21 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#6  0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#7  0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#8  0x00007f968a0286aa in start_thread (arg=0x7f94a253a700) at pthread_create.c:333
#9  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 4 (Thread 0x7f94a1b2c700 (LWP 28163)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ee4e06ed in gst_base_sink_wait_preroll () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#3  0x00007f95ee00c079 in ?? () from /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0
#4  0x00007f95ee4e2a72 in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#5  0x00007f95ee4e3ee0 in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#6  0x00007f95ef0458f8 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#7  0x00007f95ee4edb8d in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#8  0x00007f95ef0458f8 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#9  0x00007f95ee4edb8d in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#10 0x00007f95ef0458f8 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#11 0x00007f95ee4edb8d in ?? () from /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0
#12 0x00007f95ef0458f8 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#13 0x00007f95ec26c9b9 in ?? () from /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcoreelements.so
#14 0x00007f95ef075c21 in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#15 0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#16 0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#17 0x00007f968a0286aa in start_thread (arg=0x7f94a1b2c700) at pthread_create.c:333
#18 0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 3 (Thread 0x7f94a132b700 (LWP 28164)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ef075dbd in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#3  0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f968a0286aa in start_thread (arg=0x7f94a132b700) at pthread_create.c:333
#6  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 2 (Thread 0x7f94a0b2a700 (LWP 28165)):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x00007f96894ed9cf in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f95ef075dbd in ?? () from /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0
#3  0x00007f96894d02fe in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f96894cf965 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f968a0286aa in start_thread (arg=0x7f94a0b2a700) at pthread_create.c:333
#6  0x00007f968bdd4eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109

Thread 1 (Thread 0x7f968f30d800 (LWP 1873)):
[KCrash Handler]
#6  0x00007f968e2493b0 in QQmlBoundSignalExpression::function() const () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#7  0x00007f968e249450 in QQmlBoundSignalExpression::sourceLocation() const () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#8  0x00007f968e227fc8 in QQmlData::destroyed(QObject*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#9  0x00007f968c6d4424 in QObject::~QObject (this=0x15a4db0, __in_chrg=<optimized out>) at kernel/qobject.cpp:918
#10 0x00007f968e7bc2bd in QQuickItem::~QQuickItem() () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#11 0x00007f968e7d67c6 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#12 0x00007f968c6cad2b in QObjectPrivate::deleteChildren (this=this@entry=0x1c08b90) at kernel/qobject.cpp:1950
#13 0x00007f968c6d4620 in QObject::~QObject (this=<optimized out>, __in_chrg=<optimized out>) at kernel/qobject.cpp:1030
#14 0x00007f968e7bc2bd in QQuickItem::~QQuickItem() () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#15 0x00007f968e7d6b96 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#16 0x00007f968c6cd670 in QObject::event (this=0x1c08a60, e=<optimized out>) at kernel/qobject.cpp:1236
#17 0x00007f968e7ba10b in QQuickItem::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#18 0x00007f968d1eeb8c in QApplicationPrivate::notify_helper (this=this@entry=0xbe4a20, receiver=receiver@entry=0x1c08a60, e=e@entry=0x1050300) at kernel/qapplication.cpp:3720
#19 0x00007f968d1f4230 in QApplication::notify (this=0x7fffea912190, receiver=0x1c08a60, e=0x1050300) at kernel/qapplication.cpp:3503
#20 0x00007f968c69bf1b in QCoreApplication::notifyInternal (this=0x7fffea912190, receiver=0x1c08a60, event=event@entry=0x1050300) at kernel/qcoreapplication.cpp:935
#21 0x00007f968c69e057 in QCoreApplication::sendEvent (event=0x1050300, receiver=<optimized out>) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:228
#22 QCoreApplicationPrivate::sendPostedEvents (receiver=receiver@entry=0x0, event_type=event_type@entry=0, data=0xbe24c0) at kernel/qcoreapplication.cpp:1552
#23 0x00007f968c69e588 in QCoreApplication::sendPostedEvents (receiver=receiver@entry=0x0, event_type=event_type@entry=0) at kernel/qcoreapplication.cpp:1410
#24 0x00007f968c6f2e73 in postEventSourceDispatch (s=0xc3b180) at kernel/qeventdispatcher_glib.cpp:271
#25 0x00007f96894a8ff7 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#26 0x00007f96894a9250 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#27 0x00007f96894a92fc in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#28 0x00007f968c6f327f in QEventDispatcherGlib::processEvents (this=0xc4a6b0, flags=...) at kernel/qeventdispatcher_glib.cpp:418
#29 0x00007f968c69975a in QEventLoop::exec (this=this@entry=0x7fffea90ee80, flags=..., flags@entry=...) at kernel/qeventloop.cpp:204
#30 0x00007f968d3e2e6d in QDialog::exec (this=0x116ceb0) at dialogs/qdialog.cpp:541
#31 0x00007f9686385099 in KMessageBox::createKMessageBox (dialog=dialog@entry=0x116ceb0, buttons=buttons@entry=0x1b7a9d0, icon=..., text=..., strlist=..., ask=..., checkboxReturn=0x0, options=..., details=..., notifyType=QMessageBox::Warning) at ../../src/kmessagebox.cpp:393
#32 0x00007f9686385778 in KMessageBox::createKMessageBox (dialog=dialog@entry=0x116ceb0, buttons=buttons@entry=0x1b7a9d0, icon=icon@entry=QMessageBox::Warning, text=..., strlist=..., ask=..., checkboxReturn=0x0, options=..., details=...) at ../../src/kmessagebox.cpp:197
#33 0x00007f9686388d93 in KMessageBox::sorryInternal (dialog=0x116ceb0, text=..., caption=..., options=...) at ../../src/kmessagebox.cpp:847
#34 0x00007f9686388f07 in KMessageBox::sorry (parent=parent@entry=0x0, text=..., caption=..., options=..., options@entry=...) at ../../src/kmessagebox.cpp:853
#35 0x00007f968a66aea5 in KRun::runService (_service=..., _urls=..., window=window@entry=0x0, tempFiles=tempFiles@entry=false, suggestedFileName=..., asn=...) at ../../../src/widgets/krun.cpp:772
#36 0x00007f968a66c68c in KRun::run (_service=..., _urls=..., window=window@entry=0x0, tempFiles=tempFiles@entry=false, suggestedFileName=..., asn=...) at ../../../src/widgets/krun.cpp:703
#37 0x00007f9664c7b43a in ServiceRunner::run (this=<optimized out>, context=..., match=...) at ../../../runners/services/servicerunner.cpp:249
#38 0x00007f966cd8eb67 in Plasma::RunnerContext::run (this=0x1235f80, match=...) at ../../src/runnercontext.cpp:597
#39 0x00007f966cd90fc6 in Plasma::RunnerManager::run (this=0x11dffb0, match=...) at ../../src/runnermanager.cpp:673
#40 0x00007f966cfab62f in Milou::SourcesModel::run (this=<optimized out>, index=<optimized out>) at ../../lib/sourcesmodel.cpp:379
#41 0x00007f966cfafbdb in Milou::SourcesModel::qt_static_metacall (_o=<optimized out>, _c=<optimized out>, _id=<optimized out>, _a=0x7fffea90f760) at moc_sourcesmodel.cpp:129
#42 0x00007f966cfb0025 in Milou::SourcesModel::qt_metacall (this=0x1235670, _c=QMetaObject::InvokeMetaMethod, _id=5, _a=0x7fffea90f760) at moc_sourcesmodel.cpp:176
#43 0x00007f968e2066dd in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#44 0x00007f968e20850c in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#45 0x00007f968e208b75 in QV4::QObjectMethod::callInternal(QV4::CallData*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#46 0x00007f968e2165d8 in QV4::Runtime::callProperty(QV4::ExecutionContext*, QV4::String*, QV4::CallData*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#47 0x00007f966eb17450 in ?? ()
#48 0x00007fffea90fd40 in ?? ()
#49 0x0000000001c083b0 in ?? ()
#50 0x0003000000000001 in ?? ()
#51 0x00007f96680e9758 in ?? ()
#52 0x00007f96680f6840 in ?? ()
#53 0x00007f9600000000 in ?? ()
#54 0x0000000001161d00 in ?? ()
#55 0x00000000010a2750 in ?? ()
#56 0x00007f966eff0650 in ?? ()
#57 0x00007f966f0ae178 in ?? ()
#58 0x00007fffea90fff0 in ?? ()
#59 0x00007f968e1c96d6 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#60 0x00007f968e2165d8 in QV4::Runtime::callProperty(QV4::ExecutionContext*, QV4::String*, QV4::CallData*) () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#61 0x00007f966eb19186 in ?? ()
#62 0x0000000000000001 in ?? ()
#63 0x00007f968e7bd5ed in QQuickItem::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#64 0x55387b9105885900 in ?? ()
#65 0x4018000000000000 in ?? ()
#66 0x00000000015b2bb0 in ?? ()
#67 0x000000000107bc90 in ?? ()
#68 0x0000000000000023 in ?? ()
#69 0x00007fffea910770 in ?? ()
#70 0x00007fffea910260 in ?? ()
#71 0x0000000000000000 in ?? ()

```

---

