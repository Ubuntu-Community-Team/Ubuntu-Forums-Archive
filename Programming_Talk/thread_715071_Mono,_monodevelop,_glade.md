---
title: "Mono, monodevelop, glade"
date: 2008-03-04
forum: Programming Talk
---

### Post by fb2007 on 2008-03-04
Hi, I'm having problems with adding menubar to my project. I've created gui (mainWindow, and MenuBar) with glade gui editor and now when i try to compile file with monodevelop (using c#) i get an error:"(knjiznica_gtk:10318): libglade-WARNING **: unknown attribute `design-size' for <widget>.

(knjiznica_gtk:10318): libglade-WARNING **: Unexpected element <node> inside <widget>"


does anybody know what I'm doing wrong?

---

### Post by microfi on 2008-03-06
I've been having this kind of problem in Mono, too!
After adding a menu bar, and putting an item on it, I can't save my project. Right after pressing "Save" button, the IDE crashes.
Running from Terminal, I got:
```
Thread 1 (Thread -1210886448 (LWP 5307)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e03301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f22780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f22b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bf5844 in ?? ()
#6  0xb7bf582c in ?? ()
#7  0xb7bf5828 in ?? ()
#8  0xb7bf5824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```
Any suggestions?
Thanks!

---

### Post by aditya.rachakonda on 2008-03-10
I'm having the same problem. Segmentation fault for saving the files after adding a menu. Really weird!

---

