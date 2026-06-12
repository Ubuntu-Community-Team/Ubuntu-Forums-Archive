---
title: "Installing SdlDotNet"
date: 2010-07-02
forum: Programming Talk
---

### Post by PaulM1985 on 2010-07-02
Hi

I am trying to install sdldotnet to write some C# games using mono.  I have followed the instructions on this wiki:

[http://cs-sdl.sourceforge.net/index.php/The_absolute_newbies_guide_to_SDL.NET#Installation_Under_Linux](http://cs-sdl.sourceforge.net/index.php/The_absolute_newbies_guide_to_SDL.NET#Installation_Under_Linux)

But the example code keeps crashing with this output from the stack trace:

```

paul@paul-desktop:~/Documents/Programming/C#/Assemblies/sdldotnet-6.1.0/examples$ ./SdlDotNetExamples.sh
Stacktrace:

  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0x0006e>
  at (wrapper managed-to-native) Tao.Sdl.Sdl.SDL_MapRGBA (intptr,byte,byte,byte,byte) <0xffffffff>
  at SdlDotNet.Graphics.Surface.GetColorValue (System.Drawing.Color) <0x000eb>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Rectangle,System.Drawing.Color) <0x00087>
  at SdlDotNet.Graphics.Surface.Fill (System.Drawing.Color) <0x000ff>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Tick (object,SdlDotNet.Core.TickEventArgs) <0x0005b>
  at SdlDotNet.Core.Events.OnTick (SdlDotNet.Core.TickEventArgs) <0x0003a>
  at SdlDotNet.Core.Events.ThreadTicker () <0x000ef>
  at SdlDotNet.Core.Events.Run () <0x0002f>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Go () <0x00147>
  at SdlDotNetExamples.SdlDotNetExamplesBrowser.Main () <0x0002b>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono() [0x47b77f]
	mono() [0x4aef3f]
	/lib/libpthread.so.0(+0xf8f0) [0x7fa8e780d8f0]
	/usr/lib/libSDL-1.2.so.0(SDL_MapRGBA+0) [0x7fa8e599bf20]
	[0x40741e5e]

Debug info from gdb:

82	../sysdeps/unix/syscall-template.S: No such file or directory.
[Thread debugging using libthread_db enabled]
[New Thread 0x7fa8ddeef710 (LWP 3487)]
[New Thread 0x7fa8e609e710 (LWP 3486)]
[New Thread 0x7fa8e8354710 (LWP 3485)]
0x00007fa8e780c93d in read () at ../sysdeps/unix/syscall-template.S:82
	in ../sysdeps/unix/syscall-template.S
  4 Thread 0x7fa8e8354710 (LWP 3485)  0x00007fa8e780d11d in nanosleep ()
    at ../sysdeps/unix/syscall-template.S:82
  3 Thread 0x7fa8e609e710 (LWP 3486)  sem_wait ()
    at ../nptl/sysdeps/unix/sysv/linux/x86_64/sem_wait.S:86
  2 Thread 0x7fa8ddeef710 (LWP 3487)  0x00007fa8e780d11d in nanosleep ()
    at ../sysdeps/unix/syscall-template.S:82
* 1 Thread 0x7fa8e84fc740 (LWP 3484)  0x00007fa8e780c93d in read ()
    at ../sysdeps/unix/syscall-template.S:82

Thread 4 (Thread 0x7fa8e8354710 (LWP 3485)):
#0  0x00007fa8e780d11d in nanosleep () at ../sysdeps/unix/syscall-template.S:82
#1  0x0000000000556342 in ?? ()
#2  0x00007fa8e78049ca in start_thread (arg=<value optimised out>)
    at pthread_create.c:300
#3  0x00007fa8e72df6cd in clone ()
    at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#4  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7fa8e609e710 (LWP 3486)):
#0  sem_wait () at ../nptl/sysdeps/unix/sysv/linux/x86_64/sem_wait.S:86
#1  0x00000000004e4aaa in ?? ()
#2  0x0000000000505035 in ?? ()
#3  0x0000000000570073 in ?? ()
#4  0x000000000058de21 in ?? ()
#5  0x00007fa8e78049ca in start_thread (arg=<value optimised out>)
    at pthread_create.c:300
#6  0x00007fa8e72df6cd in clone ()
    at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#7  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7fa8ddeef710 (LWP 3487)):
#0  0x00007fa8e780d11d in nanosleep () at ../sysdeps/unix/syscall-template.S:82
#1  0x00007fa8e59cd004 in SDL_Delay () from /usr/lib/libSDL-1.2.so.0
#2  0x00007fa8e59cd042 in ?? () from /usr/lib/libSDL-1.2.so.0
#3  0x00007fa8e5981295 in ?? () from /usr/lib/libSDL-1.2.so.0
#4  0x00007fa8e59cac79 in ?? () from /usr/lib/libSDL-1.2.so.0
#5  0x00007fa8e78049ca in start_thread (arg=<value optimised out>)
    at pthread_create.c:300
#6  0x00007fa8e72df6cd in clone ()
    at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#7  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fa8e84fc740 (LWP 3484)):
#0  0x00007fa8e780c93d in read () at ../sysdeps/unix/syscall-template.S:82
#1  0x000000000047b8f4 in ?? ()
#2  0x00000000004aef3f in ?? ()
#3  <signal handler called>
#4  0x00007fa8e599bf20 in SDL_MapRGBA () from /usr/lib/libSDL-1.2.so.0
#5  0x0000000040741e5e in ?? ()
#6  0x0000000001e7ad20 in ?? ()
#7  0x0000000000000010 in ?? ()
#8  0x00000000000001f4 in ?? ()
#9  0x00007fa8e8338e80 in ?? ()
#10 0x00000000000001f3 in ?? ()
#11 0x00007fff7d238660 in ?? ()
#12 0x00007fff7d238530 in ?? ()
#13 0x0000000000000010 in ?? ()
#14 0x00000000000001f4 in ?? ()
#15 0x00007fa8e8338e80 in ?? ()
#16 0x00007fa8e8338e80 in ?? ()
#17 0x0000000040741d9c in ?? ()
#18 0xffffffffffffff00 in ?? ()
#19 0x01fb239000007fa8 in ?? ()
#20 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
paul@paul-desktop:~/Documents/Programming/C#/Assemblies/sdldotnet-6.1.0/examples$ 

```

Anyone got any ideas on this?  Alternatively, can anyone recommend a cross platform C# library that I can use to create games with.  I want to use sprites like in SDL to create a cartoony beat em up.

Paul

---

### Post by Letrazzrot on 2010-07-02
I've done some searching for a Mono-friendly entry-level game/graphics API lately as well, and didn't have much luck.  It seems that, if you want to program games for Linux, C++ or Python is the easier way to go at the moment.

SDL.Net development seems to have stopped or at least greatly slowed, as far as I can tell.

I had some trouble before with getting various libraries to work, but that was under 64-bit linux, so perhaps check to see if you have the correct libraries installed (i.e. Tao.SDL).

A couple of other libraries that are purportedly Mono-friendly that you may want to check out:

[http://code.google.com/p/monoxna/](http://code.google.com/p/monoxna/) (Supposedly XNA ported to Mono)
[http://www.opentk.com/](http://www.opentk.com/) (OpenTK 3d graphics library wrapping OpenGL)
[http://www.agatelib.org/](http://www.agatelib.org/) (Agate Lib, 2D graphics built over OpenTK)

---

### Post by PaulM1985 on 2010-07-03
Thanks for the response.  Ideally I want to work on something cross platform.  I know C# and Java pretty well but I thought that C# would be better for distributing.  I'll have a look into Java and see if there are any similar tools available.

Paul

---

### Post by Letrazzrot on 2010-07-03
Well, you could always use an OpenGL wrapper (OpenTK appears to be somewhat mature and active, there is even an OpenTK GTK# widget that would be useful for tool development) - it's just a little more work getting a 2D engine built on top of a 3D engine, especially if it's something you've never done before.

I've even considered putting together a minimal C# 2D (or 2.5D) engine under Mono, but the task seems rather daunting at the moment, especially since I'm no whiz at OpenGL myself.  That and I don't particular enjoy writing engine code.
 
I'm not sure about Java, I've never really worked with it much, and I don't know what's available out there.

If you (or anyone else) *do* find a decent 2D oriented library accessible from a managed language in Linux (other that PyGame, which does look interesting), I'd be happy to know about it.

Good luck!

---

### Post by phrostbyte on 2010-07-03
Mono has the Tao framework. You might want to look at Ogre.NET too. Although realistically, as the other guy has said C++ and Python are probably better options. Java is alright too, because JMonkeyEngine is pretty decent and allows you to make web games also.

---

