---
title: "[SOLVED] 2D or maybe 3D effects?"
date: 2008-04-17
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-17
C++/SDL/OpenGL: I have been working on a game, and I have decided to start putting effort into special effects... specifically laser effects and explosion effects, thought I wouln't rule anything out yet. My knowledge of such effects is *so* limited, that if I were left to myself I probably wouldn't be able to come up with anything mildly impressive. I am currently writing my game to use SDL for rendering (with SDL_GFX), but I am also intending to eventually have as an alternative rendering mode, and am not afraid to use only, OpenGL. So, does anyone know of any code, or examples with code, or something, where I could get some decent 2D or 3D effects that could be used by SDL or OpenGL?

---

### Post by Wybiral on 2008-04-17
It sounds like the effects you're interested in would probably require a particle engine. There are plenty of particle tutorials online. In OpenGL it's usually just a matter or blending a quad with a texture and moving the particles around (for instance, and explosion or fire).

---

### Post by Zeotronic on 2008-04-17
Ok, I will pursue making a particle engine... but are there any other kinds of effects that might be useful?

---

### Post by heikaman on 2008-04-17
I really recommend this site 

[http://www.swiftless.com//tutorials/opengl/opengltuts.html](http://www.swiftless.com//tutorials/opengl/opengltuts.html)

There are tutorials about :
[INDENT]1- particle engine as **Wybiral** suggested
2-reflections
3-Terrain generation
4- Fog "Really coool"
and more.[/INDENT]

I hope It's useful

---

