---
title: "Problem with SDL + OpenGL and Full Screen Mode"
date: 2007-10-30
forum: Programming Talk
---

### Post by GenuineXP on 2007-10-30
I've been working with a game engine I've been developing and I've run into a strange problem with SDL and OpenGL. When I run applications in full screen mode and then quit, my desktop environment doesn't switch back to the original resolution and my mouse is magically disconnected (I'm not sure if it's physically disconnected, but mouse movement and button clicks do nothing; the cursor just sits there).

This is very annoying. Could I be forgetting to do something when the program ends? I call SDL_Quit() and several other library closing functions, and I'm pretty sure OpenGL requires no special calls to terminating functions. It seems to work on Windows systems.

Any ideas? This is quite annoying, since I usually have to press Ctrl+Alt+Backspace and log back in!

Thanks!

Update: When I tell the engine to show the system cursor, my mouse works just fine when the program exits, but the resolution doesn't change! Instead, the screen is "zoomed" and follows the mouse cursor! Strange...

---

### Post by dataw0lf on 2007-10-30
SDL_Quit() should do the cleanup for you.  Do you have any sample code I can look at?

---

### Post by Wybiral on 2007-10-30
It sounds like something isn't being freed (it's happened to me when I forget to use SDL_Quit()), could you post the code?

---

### Post by GenuineXP on 2007-10-30
I never even thought that a missed call to SDL_Quit() would be the problem, but it is! It turns out I have a cyclic reference problem between smart pointers that prevented an engine kernel object from destructing (and that destructor ultimately calls SDL_Quit() )!

That should probably fix the problem (among others...). Thanks for the help. :-)

---

### Post by dataw0lf on 2007-10-30
God, reference counting bugs can be a pain.  Best of luck! :)

---

### Post by kavithabangera on 2008-09-04
Do you know the difference between sdl and opengl?

which is the best among both the libraries?

---

### Post by Zugzwang on 2008-09-04
> **kavithabangera said:**
> Do you know the difference between sdl and opengl?

which is the best among both the libraries?
SDL is for cross-platform access to sound, graphics, keyboard, mouse, etc. as needed for multimedia applications. However, no 3D acceleration is included.

OpenGL is for using the 3D acceleration (or drawing 3D stuff in software) of your GFX card.

For most applications, the question which is best is not answerable (makes no sense). For all others, it depends on what you are trying to do.

BTW, if you have a question unrelated to a thread, start a new one please!

---

### Post by cb951303 on 2008-09-04
#include <stdlib.h>
...
...
atexit(SDL_Quit);



so you never forget....

---

### Post by Mickeysofine1972 on 2008-09-04
> **cb951303 said:**
> #include <stdlib.h>
...
...
atexit(SDL_Quit);



so you never forget....

I seem to remember that this is the preferred method on the SDL website too.

Mike

---

### Post by rnodal on 2008-09-06
Just a friendly heads up. SDL_Quit last time time I checked use exit() instead of return() which could be a problem if your doing some sort of memory management and SDL quits before your final code gets executed. I still question their decision on using exit instead of return.

-r

---

