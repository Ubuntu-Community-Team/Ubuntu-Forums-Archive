---
title: "Problem with starting f-spot"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by yadayada2 on 2008-09-21
Hi,

f-spot won't start up. I have already reinstalled it, doesn't change anything.

Here is what the shell says:

> f-spot                                                        < ~

(f-spot:6617): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(f-spot:6617): Gdk-WARNING **: locale not supported by C library
Starting new FSpot server
f-spot: ../../src/xcb_io.c:350: _XReply: Assertion `!dpy->xcb->reply_data' failed.
Stacktrace:

  at (wrapper managed-to-native) GdkGlx.Context.glXCreateContext (intptr,intptr,System.Runtime.InteropServices.HandleRef,bool) <0x00012>
  at (wrapper managed-to-native) GdkGlx.Context.glXCreateContext (intptr,intptr,System.Runtime.InteropServices.HandleRef,bool) <0xffffffff>
  at GdkGlx.Context..ctor (Gdk.Screen,GdkGlx.Context,int[]) <0x003d6>
  at GdkGlx.Context..ctor (Gdk.Screen,int[]) <0x00027>
  at FSpot.PhotoImageView.HandleRealized (object,System.EventArgs) <0x00078>
  at FSpot.PhotoImageView..ctor (FSpot.BrowsablePointer) <0x0016f>
  at FSpot.PhotoView..ctor (FSpot.IBrowsableCollection) <0x00371>
  at MainWindow..ctor (Db) <0x01eec>
  at FSpot.Core.get_MainWindow () <0x00048>
  at FSpot.Core.Organize () <0x00012>
  at FSpot.Driver.Main (string[]) <0x01420>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x51bb67]
	/lib/libpthread.so.0 [0x7f51c17327d0]
	/lib/libc.so.6(gsignal+0x35) [0x7f51c1173095]
	/lib/libc.so.6(abort+0x110) [0x7f51c1174af0]
	/lib/libc.so.6(__assert_fail+0xef) [0x7f51c116c2df]
	/usr/lib/libX11.so.6(_XReply+0x376) [0x7f51bb3bb1b6]
	/usr/lib/libX11.so.6(XQueryExtension+0xc2) [0x7f51bb3a9532]
	/usr/lib/libX11.so.6(XInitExtension+0x24) [0x7f51bb39e2d4]
	/usr/lib/libXext.so.6(XextAddDisplay+0x59) [0x7f51b9ec7c09]
	/usr/lib64/xorg/libGL.so.1(XF86DRICreateContextWithConfig+0x19c) [0x7f51ae42181c]
	/usr/lib/dri/fglrx_dri.so [0x7f51adf39a28]
	/usr/lib64/xorg/libGL.so.1 [0x7f51ae3fc656]
	/usr/lib64/xorg/libGL.so.1(glXCreateContext+0x23) [0x7f51ae3fcaa3]
	[0x4137a028]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f51c240d7a0 (LWP 6617)]
[New Thread 0x412be950 (LWP 6626)]
[New Thread 0x42f2a950 (LWP 6625)]
[New Thread 0x41add950 (LWP 6620)]
[New Thread 0x4087d950 (LWP 6619)]
[New Thread 0x41631950 (LWP 6618)]
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
(no debugging symbols found)
(no debugging symbols found)
0x00007f51c1211da2 in select () from /lib/libc.so.6
  6 Thread 0x41631950 (LWP 6618)  0x00007f51c1731e81 in nanosleep ()
   from /lib/libpthread.so.0
  5 Thread 0x4087d950 (LWP 6619)  0x00007f51c172eb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  4 Thread 0x41add950 (LWP 6620)  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  3 Thread 0x42f2a950 (LWP 6625)  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x412be950 (LWP 6626)  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f51c240d7a0 (LWP 6617)  0x00007f51c1211da2 in select ()
   from /lib/libc.so.6

Thread 6 (Thread 0x41631950 (LWP 6618)):
#0  0x00007f51c1731e81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f51c172a3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f51c1218b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x4087d950 (LWP 6619)):
#0  0x00007f51c172eb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f51c172a3f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f51c1218b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 4 (Thread 0x41add950 (LWP 6620)):
#0  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x0000000000483323 in ?? ()
#5  0x0000000041b09b96 in ?? ()
#6  0x000000004159f7bb in ?? ()
#7  0x00007f51b5a97f50 in ?? ()
#8  0x0000000041adce50 in ?? ()
#9  0x0000000041adcd50 in ?? ()
#10 0x0000000000e99ee0 in ?? ()
#11 0x0000000000000002 in ?? ()
#12 0x00007f51be86d2a8 in ?? ()
#13 0x0000000041b09b2e in ?? ()
#14 0x00007f51b5a97f50 in ?? ()
#15 0x0000000041adce50 in ?? ()
#16 0x0000000041adcd80 in ?? ()
#17 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x42f2a950 (LWP 6625)):
#0  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x00000000004827ea in ?? ()
#5  0x0000000042d26b30 in ?? ()
#6  0x0000000042f29e20 in ?? ()
#7  0xffffffffffffffff in ?? ()
#8  0x00000000016ec420 in ?? ()
#9  0x00000000007e5ba8 in ?? ()
#10 0x00007f51c23fc000 in ?? ()
#11 0x0000000042d26adb in ?? ()
#12 0x0000000042f29f68 in ?? ()
#13 0x0000000042f29eb0 in ?? ()
#14 0x0000000042f29db0 in ?? ()
#15 0x00007f51b5a9acf0 in ?? ()
#16 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x412be950 (LWP 6626)):
#0  0x00007f51c172ee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x00000000004827ea in ?? ()
#5  0x0000000042d26b30 in ?? ()
#6  0x0000000000000001 in ?? ()
#7  0x0000000042d26a8a in ?? ()
#8  0x00000000016e6ed0 in ?? ()
#9  0x00000000016e6ed0 in ?? ()
#10 0x00000000412bde30 in ?? ()
#11 0x0000000042d26adb in ?? ()
#12 0x00000000412bdf68 in ?? ()
#13 0x00000000412bdeb0 in ?? ()
#14 0x00000000412bdda0 in ?? ()
#15 0x00007f51b5a9ab80 in ?? ()
#16 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f51c240d7a0 (LWP 6617)):
#0  0x00007f51c1211da2 in select () from /lib/libc.so.6
#1  0x00007f51c1baeccc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007f51c1baf0a8 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x000000000051bbf9 in ?? ()
#4  <signal handler called>
#5  0x00007f51c1173095 in raise () from /lib/libc.so.6
#6  0x00007f51c1174af0 in abort () from /lib/libc.so.6
#7  0x00007f51c116c2df in __assert_fail () from /lib/libc.so.6
#8  0x00007f51bb3bb1b6 in _XReply () from /usr/lib/libX11.so.6
#9  0x00007f51bb3a9532 in XQueryExtension () from /usr/lib/libX11.so.6
#10 0x00007f51bb39e2d4 in XInitExtension () from /usr/lib/libX11.so.6
#11 0x00007f51b9ec7c09 in XextAddDisplay () from /usr/lib/libXext.so.6
#12 0x00007f51ae42181c in XF86DRICreateContextWithConfig ()
   from /usr/lib64/xorg/libGL.so.1
#13 0x00007f51adf39a28 in ?? () from /usr/lib/dri/fglrx_dri.so
#14 0x00007f51ae3fc656 in ?? () from /usr/lib64/xorg/libGL.so.1
#15 0x00007f51ae3fcaa3 in glXCreateContext () from /usr/lib64/xorg/libGL.so.1
#16 0x000000004137a028 in ?? ()
#17 0x0000000000000000 in ?? ()
#0  0x00007f51c1211da2 in select () from /lib/libc.so.6


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

[1]    6617 abort      f-spot


How should I proceed?

---

### Post by yadayada2 on 2008-09-22
bump

---

### Post by Orange_and_Green on 2008-09-22
Hello :KS

I am not sure, but since the errors mention OpenGL, maybe the problem could be related to that... A few ideas:

1) Are you using a proprietary driver? Do you know the model of your video card?

2) Are you running desktop effects? Do the problems persist if you disable them?

3) Does f-spot still not start if you run it in safe graphics mode?

EDIT - (aeiah definitely has a point...:)) From your nickname I assume you are in Japan, I have a Japanese locale at home and f-spot does work there, albeit a little slow. May I ask what you use f-spot for? I have found gthumb to be significantly faster than both f-spot and image viewer, could it be a viable alternative to you?

I wish you the best of luck :KS

---

### Post by aeiah on 2008-09-22
well, its a locale error. is ubuntu set to a minority language or region? does this happen with anything else, or do you have other strange language or location based errors or glitches?

---

### Post by yadayada2 on 2008-09-22
I have locale related errors with nearly every app I start. But other apps won't crash, so I didn't bother. What should I do?

---

### Post by yadayada2 on 2008-09-25
bump (about the locales)

---

### Post by yadayada2 on 2008-10-03
bump

---

