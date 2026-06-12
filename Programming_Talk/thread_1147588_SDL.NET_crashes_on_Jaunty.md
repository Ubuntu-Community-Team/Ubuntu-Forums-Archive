---
title: "SDL.NET crashes on Jaunty"
date: 2009-05-03
forum: Programming Talk
---

### Post by jespdj on 2009-05-03
I'm trying to follow [this programming tutorial](http://www.tuxradar.com/content/hudzilla-coding-academy-project-four), but the [SDL.NET](http://cs-sdl.sourceforge.net/index.php/Main_Page) stuff doesn't work. If I try to run the examples included with SDL.NET, it crashes with a stack trace on my system (64-bit Jaunty).

Did anybody here try SDL.NET, and do you also have problems with it?

```
jesper@jesper-laptop:~/Projects/sdldotnet-6.1.0/examples$ sh ./SdlDotNetExamples.sh
Stacktrace:

  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0x00088>
  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0xffffffff>
  at SdlDotNet.Graphics.Surface.GetColorValue (System.Drawing.Color) <0x0011b>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Rectangle,System.Drawing.Color) <0x00123>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Color) <0x001df>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Tick (object,SdlDotNet.Core.TickEventArgs) <0x0004b>
  at SdlDotNet.Core.Events.OnTick (SdlDotNet.Core.TickEventArgs) <0x0003a>
  at SdlDotNet.Core.Events.ThreadTicker () <0x000e3>
  at SdlDotNet.Core.Events.Run () <0x0002f>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Go () <0x00177>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Main () <0x00033>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x429e65]
	mono [0x44ba7d]
	/lib/libpthread.so.0 [0x7f832200a080]
	/usr/lib/libSDL-1.2.so.0(SDL_MapRGBA+0) [0x7f832020b460]
	[0x4126d3d8]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f8322cec730 (LWP 5506)]
[New Thread 0x7f8317bf7950 (LWP 5512)]
[New Thread 0x7f83208ed950 (LWP 5508)]
[New Thread 0x7f8322cf7950 (LWP 5507)]
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
0x00007f8322008edb in read () from /lib/libpthread.so.0
  4 Thread 0x7f8322cf7950 (LWP 5507)  0x00007f83220097e1 in nanosleep () from /lib/libpthread.so.0
  3 Thread 0x7f83208ed950 (LWP 5508)  0x00007f83220062e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x7f8317bf7950 (LWP 5512)  0x00007f83220097e1 in nanosleep () from /lib/libpthread.so.0
  1 Thread 0x7f8322cec730 (LWP 5506)  0x00007f8322008edb in read () from /lib/libpthread.so.0

Thread 4 (Thread 0x7f8322cf7950 (LWP 5507)):
#0  0x00007f83220097e1 in nanosleep () from /lib/libpthread.so.0
#1  0x0000000000503be2 in ?? ()
#2  0x00007f83220023ba in start_thread () from /lib/libpthread.so.0
#3  0x00007f8321ae9fcd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7f83208ed950 (LWP 5508)):
#0  0x00007f83220062e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x0000000000506815 in ?? ()
#2  0x0000000000508f8f in ?? ()
#3  0x000000000052123d in ?? ()
#4  0x0000000000496d33 in ?? ()
#5  0x00000000004b52d3 in ?? ()
#6  0x000000000051d81b in ?? ()
#7  0x000000000053a1c2 in ?? ()
#8  0x00007f83220023ba in start_thread () from /lib/libpthread.so.0
#9  0x00007f8321ae9fcd in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f8317bf7950 (LWP 5512)):
#0  0x00007f83220097e1 in nanosleep () from /lib/libpthread.so.0
#1  0x00007f8320238d54 in SDL_Delay () from /usr/lib/libSDL-1.2.so.0
#2  0x00007f8320238d92 in ?? () from /usr/lib/libSDL-1.2.so.0
#3  0x00007f83201f04c7 in ?? () from /usr/lib/libSDL-1.2.so.0
#4  0x00007f8320235e29 in ?? () from /usr/lib/libSDL-1.2.so.0
#5  0x00007f83220023ba in start_thread () from /lib/libpthread.so.0
#6  0x00007f8321ae9fcd in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f8322cec730 (LWP 5506)):
#0  0x00007f8322008edb in read () from /lib/libpthread.so.0
#1  0x0000000000429f6c in ?? ()
#2  0x000000000044ba7d in ?? ()
#3  <signal handler called>
#4  0x00007f832020b460 in SDL_MapRGBA () from /usr/lib/libSDL-1.2.so.0
#5  0x000000004126d3d8 in ?? ()
#6  0x00000000025740c0 in ?? ()
#7  0x026e6e8000007f83 in ?? ()
#8  0x00000000000000ff in ?? ()
#9  0x00000000026a2740 in ?? ()
#10 0x0000000000000010 in ?? ()
#11 0x00007fff2ad0a8d0 in ?? ()
#12 0x00007fff2ad0a6f0 in ?? ()
#13 0x00000000026e5580 in ?? ()
#14 0x00007f83208efd80 in ?? ()
#15 0x026e6e8000007f83 in ?? ()
#16 0x00007f831ecc6e80 in ?? ()
#17 0x000000004126d350 in ?? ()
#18 0x00000000026b00c8 in ?? ()
#19 0x00000000000000ff in ?? ()
#20 0x00007fff2ad0a8d0 in ?? ()
#21 0x000000004126d2ec in ?? ()
#22 0x00007fff2ad0a8e0 in ?? ()
#23 0x000000ff2ad0a890 in ?? ()
#24 0x00007f8300000000 in ?? ()
#25 0x00000000026e6e80 in ?? ()
#26 0x00000226000002e4 in ?? ()
#27 0x0000000000000b90 in ?? ()
#28 0x00007f831c368000 in ?? ()
#29 0x00007f8300000000 in ?? ()
#30 0x0000000000000000 in ?? ()
#0  0x00007f8322008edb in read () from /lib/libpthread.so.0

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

---

### Post by yannos on 2009-05-05
I got a very similar problem with a little app I'm writing using sdl.net. I got this when trying to call Fill() on a surface:
```
at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0x00088>
  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0xffffffff>
  at SdlDotNet.Graphics.Surface.GetColorValue (System.Drawing.Color) <0x00122>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Rectangle,System.Drawing.Color) <0x00183>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Color) <0x001d9>
  at GameTemplate.Program.Tick (object,SdlDotNet.Core.TickEventArgs) [0x0001a] in Program.cs:54
  at SdlDotNet.Core.Events.OnTick (SdlDotNet.Core.TickEventArgs) <0x0003e>
  at SdlDotNet.Core.Events.ThreadTicker () <0x000d6>
  at SdlDotNet.Core.Events.Run () <0x0002a>
  at GameTemplate.Program.Init () [0x000da] in Program.cs:43
  at GameTemplate.Program.Main (string[]) [0x00000] in Program.cs:16
  at (wrapper runtime-invoke) GameTemplate.Program.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/mono [0x529d21]
	/usr/bin/mono [0x43f99d]
	/lib/libpthread.so.0 [0x7fae3d1440f0]
	/usr/lib/libSDL-1.2.so.0(SDL_MapRGBA+0) [0x7fae3b4642f0]
	[0x418db578]
```

---

### Post by jespdj on 2009-05-06
Maybe SDL.NET for some reason doesn't work with the version of Mono that's included with Jaunty. Are you also using Jaunty?

On the SDL.NET forums there is [a post](http://cs-sdl.sourceforge.net/forum/viewtopic.php?t=1539) of someone who seems to have a similar problem, but there's no solution posted there...

---

### Post by directhex on 2009-05-06
I suspect it's more likely to be the SDL version in Jaunty - it's dying on unmanaged pointer stuff, which makes me think (for example) that a pointer size has changed in SDL someplace compared to what's expected

---

### Post by yannos on 2009-05-06
I'm on Intrepid.

---

### Post by yannos on 2009-05-06
Could this be an 64bit problem? I have a 32bit version of libSDL-1.2.so.0 in /usr/lib32 but I don't have one of libSDL_gfx.so.4, witch seems to be implementing SDL_MapRGBA. Maybe SDL.NET needs 32bit libraries?

---

### Post by jespdj on 2009-05-06
Maybe... This is what's in my lib32 and lib64 directories:
```
jesper@jesper-laptop:/usr/lib32$ ls -l libSDL*
lrwxrwxrwx 1 root root     15 2009-04-24 20:22 libSDL-1.2.so -> libSDL-1.2.so.0
lrwxrwxrwx 1 root root     20 2009-04-24 20:22 libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.2
-rw-r--r-- 1 root root 430584 2009-02-20 04:06 libSDL-1.2.so.0.11.2
lrwxrwxrwx 1 root root     21 2009-04-24 20:22 libSDL_image-1.2.so -> libSDL_image-1.2.so.0
lrwxrwxrwx 1 root root     25 2009-04-24 20:22 libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.1.5
-rw-r--r-- 1 root root  43108 2008-02-12 04:11 libSDL_image-1.2.so.0.1.5
lrwxrwxrwx 1 root root     21 2009-04-24 20:22 libSDL_mixer-1.2.so -> libSDL_mixer-1.2.so.0
lrwxrwxrwx 1 root root     25 2009-04-24 20:22 libSDL_mixer-1.2.so.0 -> libSDL_mixer-1.2.so.0.2.6
-rw-r--r-- 1 root root 187960 2008-11-06 00:06 libSDL_mixer-1.2.so.0.2.6
lrwxrwxrwx 1 root root     19 2009-04-24 20:22 libSDL_net-1.2.so -> libSDL_net-1.2.so.0
lrwxrwxrwx 1 root root     23 2009-04-24 20:22 libSDL_net-1.2.so.0 -> libSDL_net-1.2.so.0.0.7
-rw-r--r-- 1 root root  11612 2007-10-31 14:36 libSDL_net-1.2.so.0.0.7
lrwxrwxrwx 1 root root     19 2009-04-24 20:22 libSDL_ttf-2.0.so -> libSDL_ttf-2.0.so.0
lrwxrwxrwx 1 root root     23 2009-04-24 20:22 libSDL_ttf-2.0.so.0 -> libSDL_ttf-2.0.so.0.6.3
-rw-r--r-- 1 root root  18024 2007-08-07 00:59 libSDL_ttf-2.0.so.0.6.3
jesper@jesper-laptop:/usr/lib32$ cd ../lib64
jesper@jesper-laptop:/usr/lib64$ ls -l libSDL*
lrwxrwxrwx 1 root root     20 2009-04-24 21:47 libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.2
-rw-r--r-- 1 root root 440544 2009-02-20 04:04 libSDL-1.2.so.0.11.2
-rw-r--r-- 1 root root 880216 2009-02-20 04:04 libSDL.a
-rw-r--r-- 1 root root  75846 2008-05-07 18:18 libSDL_gfx.a
-rw-r--r-- 1 root root    858 2008-05-07 18:18 libSDL_gfx.la
lrwxrwxrwx 1 root root     19 2009-05-03 16:19 libSDL_gfx.so -> libSDL_gfx.so.4.9.0
lrwxrwxrwx 1 root root     19 2009-05-03 16:19 libSDL_gfx.so.4 -> libSDL_gfx.so.4.9.0
-rw-r--r-- 1 root root  65688 2008-05-07 18:18 libSDL_gfx.so.4.9.0
lrwxrwxrwx 1 root root     25 2009-04-24 21:38 libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.1.5
-rw-r--r-- 1 root root  48744 2008-02-12 04:20 libSDL_image-1.2.so.0.1.5
-rw-r--r-- 1 root root  81120 2008-02-12 04:20 libSDL_image.a
-rw-r--r-- 1 root root    931 2008-02-12 04:20 libSDL_image.la
lrwxrwxrwx 1 root root     25 2009-05-03 16:19 libSDL_image.so -> libSDL_image-1.2.so.0.1.5
-rw-r--r-- 1 root root    794 2009-02-20 04:04 libSDL.la
-rw-r--r-- 1 root root    818 2009-02-20 04:04 libSDLmain.a
lrwxrwxrwx 1 root root     25 2009-05-03 16:19 libSDL_mixer-1.2.so.0 -> libSDL_mixer-1.2.so.0.2.6
-rw-r--r-- 1 root root 207608 2008-11-06 01:19 libSDL_mixer-1.2.so.0.2.6
-rw-r--r-- 1 root root 360970 2008-11-06 01:19 libSDL_mixer.a
-rw-r--r-- 1 root root    998 2008-11-06 01:19 libSDL_mixer.la
lrwxrwxrwx 1 root root     25 2009-05-03 16:19 libSDL_mixer.so -> libSDL_mixer-1.2.so.0.2.6
lrwxrwxrwx 1 root root     23 2009-05-03 16:19 libSDL_net-1.2.so.0 -> libSDL_net-1.2.so.0.0.7
-rw-r--r-- 1 root root  14976 2007-11-02 20:04 libSDL_net-1.2.so.0.0.7
-rw-r--r-- 1 root root  18634 2007-11-02 20:04 libSDL_net.a
-rw-r--r-- 1 root root    849 2007-11-02 20:04 libSDL_net.la
lrwxrwxrwx 1 root root     23 2009-05-03 16:19 libSDL_net.so -> libSDL_net-1.2.so.0.0.7
lrwxrwxrwx 1 root root     20 2009-05-03 16:19 libSDL.so -> libSDL-1.2.so.0.11.2
lrwxrwxrwx 1 root root     23 2009-05-03 16:19 libSDL_ttf-2.0.so.0 -> libSDL_ttf-2.0.so.0.6.3
-rw-r--r-- 1 root root  22128 2007-08-07 01:07 libSDL_ttf-2.0.so.0.6.3
-rw-r--r-- 1 root root  22328 2007-08-07 01:07 libSDL_ttf.a
-rw-r--r-- 1 root root    877 2007-08-07 01:07 libSDL_ttf.la
lrwxrwxrwx 1 root root     23 2009-05-03 16:19 libSDL_ttf.so -> libSDL_ttf-2.0.so.0.6.3

```

---

### Post by directhex on 2009-05-06
> **yannos said:**
> Could this be an 64bit problem? I have a 32bit version of libSDL-1.2.so.0 in /usr/lib32 but I don't have one of libSDL_gfx.so.4, witch seems to be implementing SDL_MapRGBA. Maybe SDL.NET needs 32bit libraries?

64-bit Mono needs 64-bit native libraries (i.e. 64-bit SDL). Whether or not SDL.NET is buggy and does not work with 64-bit SDL is another question

---

### Post by yannos on 2009-05-07
Yesterday I decided to compile mono 2.4 by hand following this guide: [http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/](http://www.centriment.com/2009/04/01/building-mono-24-from-source-on-ubuntu-810/). It still crash with nearly the exact same backtrace :(

At least now I can debug, since I have monodevelop 2.0 installed, but I don't really understand the crash. It's in Color.cs, in the FromArgb function:

```

public static Color FromArgb (int alpha, int red, int green, int blue)
{
  CheckARGBValues (alpha, red, green, blue);
  Color color = new Color ();
  color.state = (short) ColorType.ARGB;
  color.Value = (int)((uint) (alpha << 24) + (red << 16) + (green << 8) + blue);
  return color;
}

```

Whenever you assign color.Value to something, it crashes. Value is declare as "internal long". I'm still pretty much a noob when it comes to C#, so I don't know what to make of all this.

---

### Post by jespdj on 2009-05-07
The problem is not in the C# code, but in some underlying native C or C++ code in one of the SDL.NET libraries. It's probably written in such a way that it does not work properly on a 64-bit system...

---

### Post by jespdj on 2009-05-08
I added a bug report here: [https://sourceforge.net/tracker/?func=browse&group_id=52340&atid=466516](https://sourceforge.net/tracker/?func=browse&group_id=52340&atid=466516)

---

### Post by yannos on 2009-05-09
I took some time this morning to investigate this issue a bit more. Could it be a problem related to the version of libsdl installed? According to Synaptic, I have 1.2.13-2ubuntu1, yet sdl-config --version outputs 1.2.12. I'm pretty sure Tao.Sdl needs 1.2.13.

---

### Post by krsco on 2012-09-19
I have the same problem. Ubuntu 12.04 Precise Pangolin 64bits.

Anyone who fixed it?

---

