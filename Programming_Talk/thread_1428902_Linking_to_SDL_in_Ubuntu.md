---
title: "Linking to SDL in Ubuntu"
date: 2010-03-13
forum: Programming Talk
---

### Post by EMR on 2010-03-13
Okay, I'm working in Code::Blocks (the version from the repository), and I'm trying to work through some SDL tutorials.  Except I'm not sure how to link correctly to .so (static library?) files.

Concisely, how do I tell the linker where to look, and what specifically to link to.  Thank you very much.  (Sorry if I'm posting this in the wrong place).

Also, regarding libsdl from the repositories, which .so do we link to?
/usr/lib/libSDL-1.2.so.0.11.1
or
/usr/lib/libSDL-1.2.so.0
?

Thanks...

---

### Post by Compyx on 2010-03-13
You link with libSDL with `sdl-config --cflags --libs`, for example:
```

gcc -o foo foo.c `sdl-config --cflags --libs`

```

A *.so file is a shared object, so you don't link it in with your object file as you would with a static library (.a), the dynamic linker does this when your application is started.

---

### Post by TheBuzzSaw on 2010-03-13
Another way is to add the shorthand names to your list of linked libraries:

```
SDLmain
SDL
```

If you have any other librares (such as SDL_image), just stick them in between those two.

---

### Post by EMR on 2010-03-13
BuzzSaw, where do I put SDL_main and SDL?  Do I put the following in my main header?
```

#include <SDLmain>
#include <SDL_image>
#include <SDL>
```

And if so, it'll dynamically link correctly?

Thanks!

---

### Post by TheBuzzSaw on 2010-03-15
No. Linking does not happen in your code. It happens in your linker settings. In Code::Blocks, go to Project > Build Options. Find the Linker Settings tab, and add the items I posted above to the Link Libraries section.

---

