---
title: "GCC gives tons of warnings about SDL without a reason"
date: 2008-11-07
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-07
I get these every time I compile ANYTHING that uses SDL. However, it still compiles everything fine.
```

arho@ohra-laptop:~/Työpöytä/C/OpenSoldat$ make
gcc -Wall -ansi -o output main.c -lGL -lGLU `sdl-config --cflags --libs`
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from stuff.c:5,
                 from main.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive

```
I suppose those those warnings are not 'caused by me. There is probably something wrong with SDL libraries, and I'm not gonna fix it, too big job. 
But is there a way to make GCC stfu about those things? They are annoying and fill up my console window when I am programming.

I want to only see errors & warnings from MY program, not some messy SDL libraries.

---

### Post by Ferrat on 2008-11-07
```
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive 
```

all the errors are the same one, sound like a comment that's missing a // or something in begin_code.h on row 94

---

### Post by crazyfuturamanoob on 2008-11-08
> **Ferrat said:**
> [code]/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive [code]

all the errors are the same one, sound like a comment that's missing a // or something in begin_code.h on row 94

That is SDL library, not my code, so I can't fix it. But is there a way to make gcc not reporting it?

---

### Post by WW on 2008-11-08
Could you show us the first 18 lines of main.c and the first 5 lines of stuff.c?

---

### Post by crazyfuturamanoob on 2008-11-08
> **WW said:**
> Could you show us the first 18 lines of main.c and the first 5 lines of stuff.c?

18 first lines from main.c
```

/*
 * This code was created by Jeff Molofee '99 
 * (ported to Linux/SDL by Ti Leggett '01)
 *
 * If you've found this code useful, please let me know.
 *
 * Visit Jeff at http://nehe.gamedev.net/
 * 
 * or for port-specific comments, questions, bugreports etc. 
 * email to leggett@eecs.tulane.edu
 */

/* screen width, height, and bit depth */
#define SCREEN_WIDTH  640
#define SCREEN_HEIGHT 480
#define SCREEN_BPP     16

#include "stuff.c"
```
I made that thing over NeHe tutorial 01, heh :)

And 5 lines from stuff.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <GL/gl.h>
#include <GL/glu.h>
#include "SDL.h"
```
I am going to make a library (stuff.c) which contains OpenGL init code for 2D and also SDL init code, plus some OpenGL drawing functions, such as drawing circles, loading textures etc etc.
This will save me from a lot typing in future, when I am making OpenGL/SDL games which all use the same code for initializing OpenGL & SDL & drawing stuff.

---

### Post by fstonedahl on 2009-01-06
I was having this same problem compiling neverball (which uses SDL)

And as far as I can see, for our own compiling purposes, there's no reason we can't just edit the offending SDL file to make the stream of warnings go away.  
I presume any changes will get overwritten the next time libsdl is updated, but since I'm only changing a comment anyway, I don't think it could possibly matter.

So what I did was:

sudo gedit /usr/include/SDL/begin_code.h

And changed line 94 from

#endif //__SYMBIAN32__

to 

#endif /* //__SYMBIAN32__ */

Looks to me like someone accidentally used a C++ style comment, which is fine for G++, but GCC isn't happy with.

I filed a BugZilla bug report over at [http://bugzilla.libsdl.org/](http://bugzilla.libsdl.org/), so hopefully they'll get that fixed for a future version.

Best regards,

~Forrest

---

### Post by dwhitney67 on 2009-01-07
The // style of comment is available for C programmers who use the 1999 ISO C standard.

Try adding -std=gnu99 as an option to your gcc command.

---

### Post by crazyfuturamanoob on 2009-01-07
> **dwhitney67 said:**
> The // style of comment is available for C programmers who use the 1999 ISO C standard.

Try adding -std=gnu99 as an option to your gcc command.

Somebody told that (std=gnu99) very long time ago already but thanks anyway.

I use always // comments, because large amounts of code can be later easily commented out with /* comments */.

Also, its faster to type // than /* and */. Why this isn't today's standard anymore?

---

### Post by dwhitney67 on 2009-01-07
> **crazyfuturamanoob said:**
> Somebody told that (std=gnu99) very long time ago already but thanks anyway.

I use always // comments, because large amounts of code can be later easily commented out with /* comments */.

Also, its faster to type // than /* and */. Why this isn't today's standard anymore?
It is today's standard.  However GCC defaults to the pre-1999 standard, perhaps as a favor to those that support legacy software applications.

Not all C compilers support the // style of comments, nor the ability to declare/initialize a variable at the closest point to where it is needed.

This code will not compile with the default setting of the GCC compiler:
```

// this is a comment
for (int i = 0; i < 10; ++i);    // variable 'i' declared inline with for-loop

```

---

