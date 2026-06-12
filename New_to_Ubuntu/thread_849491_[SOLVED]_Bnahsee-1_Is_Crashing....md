---
title: "[SOLVED] Bnahsee-1 Is Crashing..."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by kevin11951 on 2008-07-04
I went a head and compiled banshee 1 on my laptop, and it worked fine for a while, and i was messing around with some libraries, but now when i try to play music i get this error:

```
[Info  13:32:13.501] Running Banshee 1.0.0
[Info  13:32:15.064] All services are started 1.363434s
[Info  13:32:15.850] nereid Client Started

** (Nereid:8595): WARNING **: The following assembly referenced from /usr/local/lib/banshee-1/Extensions/Banshee.Podcasting.dll could not be loaded:
     Assembly:   taglib-sharp    (assemblyref_index=7)
     Version:    2.0.3.0
     Public Key: db62eba44689b5b0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/banshee-1/Extensions).


** (Nereid:8595): WARNING **: Could not load file or assembly 'taglib-sharp, Version=2.0.3.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0' or one of its dependencies.

** (Nereid:8595): WARNING **: The following assembly referenced from /usr/local/lib/banshee-1/Banshee.Core.dll could not be loaded:
     Assembly:   taglib-sharp    (assemblyref_index=6)
     Version:    2.0.3.0
     Public Key: db62eba44689b5b0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/banshee-1).


** (Nereid:8595): WARNING **: Could not load file or assembly 'taglib-sharp, Version=2.0.3.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0' or one of its dependencies.
Stacktrace:

  at Banshee.GStreamer.PlayerEngine.OnTagFound (intptr,string,GLib.Value&) [0x0000d] in /home/ksoviero/banshee-1-1.0.0/src/Backends/Banshee.GStreamer/Banshee.GStreamer/PlayerEngine.cs:289
  at Banshee.GStreamer.PlayerEngine.OnTagFound (intptr,string,GLib.Value&) [0x00000] in /home/ksoviero/banshee-1-1.0.0/src/Backends/Banshee.GStreamer/Banshee.GStreamer/PlayerEngine.cs:288
  at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnTagFound (intptr,intptr,GLib.Value&) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x0000b>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x00008>
  at Banshee.Gui.GtkBaseClient.Run () [0x00027] in /home/ksoviero/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:114
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /home/ksoviero/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) [0x00048] in /home/ksoviero/banshee-1-1.0.0/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54
  at Banshee.Gui.GtkBaseClient.Entry () [0x00024] in /home/ksoviero/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:50
  at Nereid.Client.Main (string[]) [0x0009b] in /home/ksoviero/banshee-1-1.0.0/src/Clients/Nereid/Nereid/Client.cs:77
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x51bb67]
	banshee-1 [0x43dacd]
	/lib/libpthread.so.0 [0x7f088e5027d0]
	banshee-1(mono_metadata_signature_equal+0x1a) [0x4a2e6a]
	banshee-1 [0x4aa513]
	banshee-1 [0x4aa79d]
	banshee-1 [0x4abccd]
	banshee-1 [0x4ac2f8]
	banshee-1(mono_get_method_full+0x8a) [0x4ac62a]
	banshee-1 [0x4f7842]
	banshee-1 [0x507617]
	banshee-1 [0x508cd9]
	banshee-1 [0x43fe72]
	[0x402c215b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f088f1e07a0 (LWP 8595)]
[New Thread 0x46592950 (LWP 8629)]
[New Thread 0x45d91950 (LWP 8628)]
[New Thread 0x42f0c950 (LWP 8627)]
[New Thread 0x4270b950 (LWP 8625)]
[New Thread 0x45590950 (LWP 8624)]
[New Thread 0x41153950 (LWP 8604)]
[New Thread 0x40864950 (LWP 8603)]
[New Thread 0x4313d950 (LWP 8602)]
[New Thread 0x4172c950 (LWP 8598)]
[New Thread 0x41eea950 (LWP 8597)]
[New Thread 0x413b7950 (LWP 8596)]
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
0x00007f088e966747 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
  12 Thread 0x413b7950 (LWP 8596)  0x00007f088e501e81 in nanosleep ()
   from /lib/libpthread.so.0
  11 Thread 0x41eea950 (LWP 8597)  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  10 Thread 0x4172c950 (LWP 8598)  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  9 Thread 0x4313d950 (LWP 8602)  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  8 Thread 0x40864950 (LWP 8603)  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  7 Thread 0x41153950 (LWP 8604)  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  6 Thread 0x45590950 (LWP 8624)  0x00007f088dfdfc76 in poll ()
   from /lib/libc.so.6
  5 Thread 0x4270b950 (LWP 8625)  0x00007f087adc9fc6 in ?? ()
   from /usr/lib/gstreamer-0.10/libgstmad.so
  4 Thread 0x42f0c950 (LWP 8627)  0x00007f088dfdfc76 in poll ()
   from /lib/libc.so.6
  3 Thread 0x45d91950 (LWP 8628)  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x46592950 (LWP 8629)  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f088f1e07a0 (LWP 8595)  0x00007f088e966747 in g_slice_alloc ()
   from /usr/lib/libglib-2.0.so.0

Thread 12 (Thread 0x413b7950 (LWP 8596)):
#0  0x00007f088e501e81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 11 (Thread 0x41eea950 (LWP 8597)):
#0  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 10 (Thread 0x4172c950 (LWP 8598)):
#0  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x0000000000483323 in ?? ()
#5  0x00000000419584c6 in ?? ()
#6  0x000000004048454b in ?? ()
#7  0x00007f088c92ac40 in ?? ()
#8  0x000000004172be30 in ?? ()
#9  0x000000004172bd30 in ?? ()
#10 0x00000000011d1c10 in ?? ()
#11 0x0000000000000002 in ?? ()
#12 0x00007f08876b0d48 in ?? ()
#13 0x000000004195845e in ?? ()
#14 0x00007f088c92ac40 in ?? ()
#15 0x000000004172be30 in ?? ()
#16 0x000000004172bd60 in ?? ()
#17 0x00007f088f090700 in ?? ()
#18 0x0000000000000000 in ?? ()

Thread 9 (Thread 0x4313d950 (LWP 8602)):
#0  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004cbff5 in ?? ()
#3  0x00000000004848a0 in ?? ()
#4  0x0000000041b8d64d in ?? ()
#5  0x000000004313cc20 in ?? ()
#6  0xffffffffffffffff in ?? ()
#7  0x00007f0887079c00 in ?? ()
#8  0x0000000002167760 in ?? ()
#9  0x0000000000000001 in ?? ()
#10 0x0000000000000040 in ?? ()
#11 0x0000000041b8d5eb in ?? ()
#12 0x00000000020e9e88 in ?? ()
#13 0x000000004313cc90 in ?? ()
#14 0x000000004313cbb0 in ?? ()
#15 0x000000004313cca0 in ?? ()
#16 0x00007f0887079c00 in ?? ()
#17 0xffffffffffffffff in ?? ()
#18 0x00007f0887079c00 in ?? ()
#19 0x000000004313cc90 in ?? ()
#20 0x0000000041b8d313 in ?? ()
#21 0x00007f0887079c00 in ?? ()
#22 0x0000000000000000 in ?? ()

Thread 8 (Thread 0x40864950 (LWP 8603)):
#0  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004cbff5 in ?? ()
#3  0x00000000004848a0 in ?? ()
#4  0x0000000041b8d64d in ?? ()
#5  0x0000000000000000 in ?? ()

Thread 7 (Thread 0x41153950 (LWP 8604)):
#0  0x00007f088e4fee1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb570 in ?? ()
#2  0x00000000004cbff5 in ?? ()
#3  0x00000000004848a0 in ?? ()
#4  0x0000000041b8d64d in ?? ()
#5  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x45590950 (LWP 8624)):
#0  0x00007f088dfdfc76 in poll () from /lib/libc.so.6
#1  0x00007f088e94e366 in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007f088e94e7d7 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#3  0x00007f0886bdfb80 in ?? () from /usr/lib/libORBit-2.so.0
#4  0x00007f088e971054 in ?? () from /usr/lib/libglib-2.0.so.0
#5  0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#6  0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x4270b950 (LWP 8625)):
#0  0x00007f087adc9fc6 in ?? () from /usr/lib/gstreamer-0.10/libgstmad.so
#1  0x00007f08854227e9 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#2  0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#3  0x00007f087e63d50e in ?? ()
   from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#4  0x00007f087e63ea34 in ?? ()
   from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#5  0x00007f08854227e9 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#6  0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#7  0x00007f088465d3a4 in ?? () from /usr/lib/libgsttag-0.10.so.0
#8  0x00007f08854227e9 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#10 0x00007f087c848f5e in ?? ()
   from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#11 0x00007f08854227e9 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#13 0x00007f08854227e9 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#15 0x00007f0885aca02c in ?? () from /usr/lib/libgstbase-0.10.so.0
#16 0x00007f088543cb29 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x00007f088e972bf7 in ?? () from /usr/lib/libglib-2.0.so.0
#18 0x00007f088e971054 in ?? () from /usr/lib/libglib-2.0.so.0
#19 0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#20 0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#21 0x0000000000000000 in ?? ()

Thread 4 (Thread 0x42f0c950 (LWP 8627)):
#0  0x00007f088dfdfc76 in poll () from /lib/libc.so.6
#1  0x00007f087a14228d in ?? () from /usr/lib/libpulse.so.0
#2  0x00007f087a13725a in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#3  0x00007f087a138598 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#4  0x00007f087a138650 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#5  0x00007f087a1421ad in ?? () from /usr/lib/libpulse.so.0
#6  0x00007f087a15dd0d in ?? () from /usr/lib/libpulse.so.0
#7  0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#8  0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#9  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x45d91950 (LWP 8628)):
#0  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f087a1423f4 in pa_threaded_mainloop_wait ()
   from /usr/lib/libpulse.so.0
#2  0x00007f087a379336 in ?? () from /usr/lib/gstreamer-0.10/libgstpulse.so
#3  0x00007f087eeafa49 in ?? () from /usr/lib/libgstaudio-0.10.so.0
#4  0x00007f087eebad68 in gst_ring_buffer_acquire ()
   from /usr/lib/libgstaudio-0.10.so.0
#5  0x00007f087eeb22f8 in ?? () from /usr/lib/libgstaudio-0.10.so.0
#6  0x00007f0885ac3026 in ?? () from /usr/lib/libgstbase-0.10.so.0
#7  0x00007f0885421338 in gst_pad_set_caps ()
   from /usr/lib/libgstreamer-0.10.so.0
#8  0x00007f0885414e04 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x00007f0885421338 in gst_pad_set_caps ()
   from /usr/lib/libgstreamer-0.10.so.0
#10 0x00007f0885414e04 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x00007f0885421338 in gst_pad_set_caps ()
   from /usr/lib/libgstreamer-0.10.so.0
#12 0x00007f0885414e04 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#13 0x00007f0885421338 in gst_pad_set_caps ()
   from /usr/lib/libgstreamer-0.10.so.0
#14 0x00007f088542299c in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x00007f0885422e03 in gst_pad_push () from /usr/lib/libgstreamer-0.10.so.0
#16 0x00007f087c843b22 in ?? ()
   from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#17 0x00007f088543cb29 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x00007f088e972bf7 in ?? () from /usr/lib/libglib-2.0.so.0
#19 0x00007f088e971054 in ?? () from /usr/lib/libglib-2.0.so.0
#20 0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#21 0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#22 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x46592950 (LWP 8629)):
#0  0x00007f088e4feb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f087c84361d in ?? ()
   from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#2  0x00007f088543cb29 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#3  0x00007f088e972bf7 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0x00007f088e971054 in ?? () from /usr/lib/libglib-2.0.so.0
#5  0x00007f088e4fa3f7 in start_thread () from /lib/libpthread.so.0
#6  0x00007f088dfe8b2d in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f088f1e07a0 (LWP 8595)):
#0  0x00007f088e966747 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#1  0x00007f088e96c06b in g_string_sized_new () from /usr/lib/libglib-2.0.so.0
#2  0x00007f088e97e8fe in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0x00007f088e97ed98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#4  0x000000000051bbf9 in ?? ()
#5  0x000000000043dacd in ?? ()
#6  <signal handler called>
#7  0x00000000004a2e6a in mono_metadata_signature_equal ()
#8  0x00000000004aa513 in ?? ()
#9  0x00000000004aa79d in ?? ()
#10 0x00000000004abccd in ?? ()
#11 0x00000000004ac2f8 in ?? ()
#12 0x00000000004ac62a in mono_get_method_full ()
#13 0x00000000004f7842 in ?? ()
#14 0x0000000000507617 in ?? ()
#15 0x0000000000508cd9 in ?? ()
#16 0x000000000043fe72 in ?? ()
#17 0x00000000402c215b in ?? ()
#18 0x0000000000000040 in ?? ()
#19 0x0000000001e9c430 in ?? ()
#20 0x0000000000000000 in ?? ()
#0  0x00007f088e966747 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by kevin11951 on 2008-07-04
nevermind, i fixed it by running "sudo apt-get build-dep banshee"

---

### Post by ZabiGG on 2008-07-05
Great, thanks for the tip. 

But to help us help all the other people who ask for help more efficiently, please mark your post solved.

Instructions in the SOLVED link in my signature below.

Thanks in advance and happy Ubuntuing.

Z.

---

