---
title: "SDL Segfaults on SDL_SetVideoMode"
date: 2006-09-03
forum: Programming Talk
---

### Post by enigma_0Z on 2006-09-03
Hi all, got a lovely problem here...

For no apparent reason, SDL segfaults when I attempt to set up an opengl window.

I've read aobut this particular problem on the internet, but have yet to actually find a solution... Here's code that will get you started:

```

#include <SDL.h>

int main()
{
	SDL_Init(SDL_INIT_TIMER | SDL_INIT_VIDEO | SDL_INIT_JOYSTICK);
	SDL_SetVideoMode(800, 600, 0, SDL_OPENGL | SDL_FULLSCREEN);
	SDL_Quit();
}

```

This segfaults at line 2. If I don't do SDL_OPENGL, everything works happily. 

Has anyone found a solution to this problem under Ubuntu? Thanks.

<edit>
Fixed in SDL 1.2.11. Downloaded libs & includes, ran alien on the RPM's,and everything's running like clockwork now.
</edit>

---

