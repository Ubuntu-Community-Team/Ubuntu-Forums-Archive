---
title: "problem with sdldotnet in monodevelop"
date: 2008-07-06
forum: Programming Talk
---

### Post by hyunkell on 2008-07-06
After coding a few small games in sdl, I wanted to get into sdl.net.
So I went ahead and installed mono and all the stuff from this guide:

[http://cs-sdl.sourceforge.net/index.ph/The_absolute_newbies_guide_to_SDL.NET](http://cs-sdl.sourceforge.net/index.ph/The_absolute_newbies_guide_to_SDL.NET)

Worked fine, so I fired up monodevelop, and did a few basic tutorials to get into C#.
I encountered no problems whatsoever.

My problem lies with sdl.net
It works fine, but as soon as I try to convert a surface

```
m_Background = ( new Surface( @"DemoBackground.png" )).Convert( m_VideoScreen, true, false );
```

it crashes as soon as I try to run (debug) the program:

> Stacktrace:

  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_ConvertSurface (intptr,intptr,int) <0x0000e>
  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_ConvertSurface (intptr,intptr,int) <0xffffffff>
  at SdlDotNet.Graphics.Surface.Convert (SdlDotNet.Graphics.Surface,bool,bool) <0x000d8>
  at SDL.LoadImages () [0x0001e] in /home/hyunkell/cs_test/cs_test/Main.cs:33
  at SDL.Main (string[]) [0x0001a] in /home/hyunkell/cs_test/cs_test/Main.cs:22
  at (wrapper runtime-invoke) SDL.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/mono [0x51bb67]
	/usr/bin/mono [0x43dacd]
	/lib/libpthread.so.0 [0x7f5c83f227d0]
	/usr/lib/libSDL-1.2.so.0(SDL_ConvertSurface+0x17) [0x7f5c8216dd87]
	[0x41fb4687]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f5c84c027a0 (LWP 27853)]
[New Thread 0x41b92950 (LWP 27856)]
[New Thread 0x41c9f950 (LWP 27854)]
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
0x00007f5c839cec4b in fork () from /lib/libc.so.6
  3 Thread 0x41c9f950 (LWP 27854)  0x00007f5c83f21e81 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x41b92950 (LWP 27856)  0x00007f5c83f1eb99 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f5c84c027a0 (LWP 27853)  0x00007f5c839cec4b in fork ()
   from /lib/libc.so.6

Thread 3 (Thread 0x41c9f950 (LWP 27854)):
#0  0x00007f5c83f21e81 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004b8f4f in ?? ()
#2  0x00007f5c83f1a3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f5c83a08b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x41b92950 (LWP 27856)):
#0  0x00007f5c83f1eb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004bb585 in ?? ()
#2  0x00000000004bdb37 in ?? ()
#3  0x00000000004cbc03 in ?? ()
#4  0x000000000046b3c1 in ?? ()
#5  0x00000000004855c3 in ?? ()
#6  0x00000000004cb287 in ?? ()
#7  0x00000000004e07d2 in ?? ()
#8  0x00007f5c83f1a3f7 in start_thread () from /lib/libpthread.so.0
#9  0x00007f5c83a08b2d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f5c84c027a0 (LWP 27853)):
#0  0x00007f5c839cec4b in fork () from /lib/libc.so.6
#1  0x00007f5c8439dd6d in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007f5c8439e8df in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0x00007f5c8439ed98 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#4  0x000000000051bbf9 in ?? ()
#5  0x000000000043dacd in ?? ()
#6  <signal handler called>
#7  0x00007f5c8216dd87 in SDL_ConvertSurface () from /usr/lib/libSDL-1.2.so.0
#8  0x0000000041fb4687 in ?? ()
#9  0x0000000000987d80 in ?? ()
#10 0x0000000000000001 in ?? ()
#11 0x0000000000000001 in ?? ()
#12 0x00007fff8cc1ccf0 in ?? ()
#13 0x00000000008112a0 in ?? ()
#14 0x00984ee000007f5c in ?? ()
#15 0x00000000009d7690 in ?? ()
#16 0x0000000041fb461e in ?? ()
#17 0x0000000000000001 in ?? ()
#18 0x00007fff8cc1d0e0 in ?? ()
#19 0x00007fff8cc1cec0 in ?? ()
#20 0x00007f5c823ebe80 in ?? ()
#21 0x00007f5c823ebf80 in ?? ()
#22 0x00000000009d7690 in ?? ()
#23 0x0000000000000000 in ?? ()
#0  0x00007f5c839cec4b in fork () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

I'm not really sure where to search for the problem, but I guess that there's something wrong with my setup :(

Any ideas?

Thanks,
hyu

---

### Post by Bufke on 2008-07-06
You could try running a newer version on Mono.  The version with Ubuntu is a bit old.  The installer from the Mono project is pretty easy to use. This fixed tons of problems for me.

---

### Post by hyunkell on 2008-07-07
This sounds like it may be the source of the problem indeed.
I didn't notice the version in ubuntus repositories was so old, I'll try to install the last one as soon as I get home.

Thank you for pointing this out :)

---

