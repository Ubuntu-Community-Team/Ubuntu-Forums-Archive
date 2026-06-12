---
title: "SDL.h not found"
date: 2009-05-09
forum: Programming Talk
---

### Post by Stoodle on 2009-05-09
I'm compiling a program and I have SDL and sdl_gfx installed. My problem is that I'm getting
```

/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory

```

I have absolutely no idea why because it's in the same folder as SDL.h.

---

### Post by Stoodle on 2009-05-09
Bump. I assume people have dealt with this problem before.

---

### Post by SKLP on 2009-05-09
Maybe this will help.
 sudo apt-get install libsdl-gfx1.2-dev libsdl1.2-dev

---

### Post by Stoodle on 2009-05-10
I already did that. SDL_gfxPrimitives is in the same include folder as SDL.h.

---

### Post by dwhitney67 on 2009-05-10
> **Stoodle said:**
> Bump. I assume people have dealt with this problem before.

Yes, people have been through this issue many times.  Did you do any research to find posts describing a similar problem and the solution?  I have never used SDL, but I have helped at least several other members with the exact same problem.

It would be helpful if you posted the gcc (or g++) statement that you are using to compile your code.  If indeed you have the SDL library installed, I wager that you neglected to provide the proper path for the file(s) you are including, and/or failed to provide GCC with the appropriate option indicating where the include files are stored on your system.  (Note, you will have to do something similar for the shared-object libraries).

So, in your code, files should be included in a format similar to:
```

#include <SDL/SDL_gfxPrimitives.h>

```

When calling gcc, use the following option:
```

gcc -I/usr/local/include -c myfile.c

```
This will generate the object file.  For other modules you may have, repeat the same, of course, substituting the filename.

To link:
```

gcc myfile.o [other.o] -L/usr/local/lib -lSDL -o myapp

```
As stated earlier, if you have more than one module, then substitute the [other.o] with the appropriate filename(s).

Btw, I do believe SDL comes with a pkg-config information package.  You should be able to do something like:
```

gcc myfile.c `pkg-config SDL --cflags --libraries` -o myapp

```

---

### Post by Stoodle on 2009-05-10
This is what I got. I'm using g++ because I never got around to learning how to compile with gcc.
```

g++ Core.cpp Capacitor.cpp LedLight.cpp DisplayModule.cpp Control_Switch.cpp Part.cpp Resistor.cpp SiliconDiode.cpp  -lSDL -lSDL_image -lSDL_gfx -lSDL_main
In file included from microtype.h:8,
                 from Core.cpp:15:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
Core.cpp: In function &#8216;int main(int, char**)&#8217;:
Core.cpp:118: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:126: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:134: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:142: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:156: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:164: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:172: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:180: warning: deprecated conversion from string constant to &#8216;char*&#8217;
Core.cpp:184: error: &#8216;Sleep&#8217; was not declared in this scope
Core.cpp:189: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from microtype.h:8,
                 from Part.h:10,
                 from Capacitor.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
Capacitor.cpp:4:23: error: SDL_image.h: No such file or directory
In file included from microtype.h:8,
                 from Part.h:10,
                 from LedLight.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
In file included from microtype.h:8,
                 from DisplayModule.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
DisplayModule.cpp:5:23: error: SDL_image.h: No such file or directory
In file included from microtype.h:8,
                 from Control_Switch.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
Control_Switch.cpp:5:23: error: SDL_image.h: No such file or directory
In file included from microtype.h:8,
                 from Part.h:10,
                 from Part.cpp:5:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
In file included from microtype.h:8,
                 from Resistor.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
In file included from microtype.h:8,
                 from SiliconDiode.cpp:2:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory

```When I search the SDL include folder, I get this.
```

 ls /usr/include/SDL/
begin_code.h     SDL_framerate.h           SDL_loadso.h    SDL_stdinc.h
close_code.h     SDL_getenv.h              SDL_main.h      SDL_syswm.h
SDL_active.h     SDL_gfxPrimitives_font.h  SDL_mixer.h     SDL_thread.h
SDL_audio.h      SDL_gfxPrimitives.h       SDL_mouse.h     SDL_timer.h
SDL_byteorder.h  SDL_gfxPrimitives.h~      SDL_mutex.h     SDL_ttf.h
SDL_cdrom.h      SDL.h                     SDL_name.h      SDL_types.h
SDL_config.h     SDL_imageFilter.h         SDL_opengl.h    SDL_version.h
SDL_cpuinfo.h    SDL_image.h               SDL_platform.h  SDL_video.h
SDL_endian.h     SDL_joystick.h            SDL_quit.h
SDL_error.h      SDL_keyboard.h            SDL_rotozoom.h
SDL_events.h     SDL_keysym.h              SDL_rwops.h

```See, this was for a project at school and I had already installed SDL and used it here on my Linux box. What I'm adding to it now is an extension because...it can't draw primitives...
This no such file error is occuring in a library file.
I have looked this up but I just haven't found anything.

In SDL_gfxPrimitives.h, the include is
```

#include <SDL/SDL.h>

```
Of course, this is after trying the default
```

#include "SDL.h"

```
and
```

#include "SDL/SDL.h"

```

---

### Post by geirha on 2009-05-10
> **dwhitney67 said:**
> 
```

gcc myfile.c `pkg-config SDL --cflags --libraries` -o myapp

```

```

pkg-config sdl --cflags    #for compiler flags
pkg-config sdl --libs      #for linker flags

# And all in one
gcc myfile.c $(pkg-config sdl --cflags --libs) -o myapp

```

---

### Post by Zugzwang on 2009-05-10
Note that header files are only searched for in the following directories:
[LIST]
[*]The directory from which you compile
[*]Those listed as the include paths.
[/LIST]
They are not searched for in a path relative from where they called. So I assume that you have the line "#include <SDL/SDL.h>" in your C/C++-files. This is *wrong* and leads to the errors you get. The SDL documentation states (or should state) that you have to do: "#include <SDL.h>".

In order to compile your program then, you have to add the SDL include path to your includes path, i.e. by adding the option "-I/usr/local/include/SDL" or something like that to the gcc/g++ call (or use the pkg-config approach above).

Finally: Never change files in "/usr/include" yourself. - This will lead to a mess.

---

### Post by Stoodle on 2009-05-10
I know that they come from /usr/include/SDL and they are not relative to the code. I don't have this problem with any of the other include files.

I forgot, what was the difference between <> and ""?

---

### Post by dwhitney67 on 2009-05-10
> **Stoodle said:**
> This is what I got. I'm using g++ because I never got around to learning how to compile with gcc.

GCC is the Gnu Cross Compiler, of which gcc and g++ are two of the products of this package.  If I recall, using gcc to mimic g++ can be done with 'gcc ... -lstdc++'.

```

g++ Core.cpp Capacitor.cpp LedLight.cpp DisplayModule.cpp Control_Switch.cpp Part.cpp Resistor.cpp SiliconDiode.cpp  -lSDL -lSDL_image -lSDL_gfx -lSDL_main
In file included from microtype.h:8,
                 from Core.cpp:15:
/usr/local/include/SDL/SDL_gfxPrimitives.h:17:17: error: SDL.h: No such file or directory
...

```
> **Stoodle said:**
> 
When I search the SDL include folder, I get this.

```

 ls /usr/include/SDL/
...

```

This is not the folder that gcc is seeing.  You're looking at /usr/include/SDL (which btw, is the typical install directory for the SDL headers), and the compiler is looking at /usr/local/include.

Determine where your SDL headers/libraries are located at, and tell this too 'g++'.  See geirha's post.

---

### Post by Stoodle on 2009-05-10
Egad! Why would they be in different locations? Thanks though. I'm going to try it.

---

### Post by Stoodle on 2009-05-10
Hooray! I used 
```

 g++ Core.cpp Capacitor.cpp LedLight.cpp DisplayModule.cpp Control_Switch.cpp Part.cpp Resistor.cpp SiliconDiode.cpp  -lSDL -lSDL_image -lSDL_gfx -lSDL_main -I/usr/include/SDL

```
That is, I changed the path of the include files with -I. Very nice. Thanks guys.

---

### Post by Sockerdrickan on 2009-05-11
The last flag really should not be needed if you use #include <SDL/SDL.h>

---

### Post by Zugzwang on 2009-05-11
> **Tux0r said:**
> The last flag really should not be needed if you use #include <SDL/SDL.h>

...unless "SDL.h" in turn includes other .h files in the "SDL" directory without referencing to them in the directory "SDL", which it seems to do, so adding the "SDL" path to the include paths this is the way to go.

---

### Post by Stoodle on 2009-05-11
How do I mark this as solved?

---

### Post by Zugzwang on 2009-05-12
> **Stoodle said:**
> How do I mark this as solved?

Find the "Thread Tools" on this page (CTRL+F). Click onto it and you will see an option to mark this thread as being solved.

---

### Post by geirha on 2009-05-12
> **Zugzwang said:**
> Find the "Thread Tools" on this page (CTRL+F). Click onto it and you will see an option to mark this thread as being solved.

Isn't the "mark as solved" and "thank post" features still disabled? I think only moderators/administrator can mark a post as solved by changing the thread title.

---

### Post by Stoodle on 2009-05-12
That's what I thought. I didn't see it.

---

