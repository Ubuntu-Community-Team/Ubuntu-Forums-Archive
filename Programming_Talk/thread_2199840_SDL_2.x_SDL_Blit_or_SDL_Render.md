---
title: "SDL 2.x SDL_Blit or SDL_Render?"
date: 2014-01-16
forum: Programming Talk
---

### Post by slooksterpsv on 2014-01-16
I'm making a game in SDL, I moved from SDL 1.2 to SDL 2.0 because trying to setup 1.xx in Windows just didn't work as well as I thought it would so I'm using SDL 2.0 with Orwell Dev-C++; and in Linux just using Scratchpad in Elementary OS. So here's my question:

I'm used to using SDL_BlitSurface rather than using SDL_RenderCopy. The main difference? SDL_RenderCopy keeps what I render closer to the GPU memory where Blit copies to RAM then presents it to the screen. Now my issue is this. What's better to use? I know that RenderCopy would most likely be faster, but Blit seems like it would be more compatible.

Is there really a big difference? Should I use one or the other? Or should I wait till I've implemented everything and try to see what works better?

RenderCopy does require a couple more functions to use
Surface -> Texture -> Renderer
Where blit did this
Surface -> Screen

Either way I still have to load a texture as a surface and go from there.

---

