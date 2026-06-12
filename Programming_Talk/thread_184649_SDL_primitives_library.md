---
title: "SDL primitives library"
date: 2006-05-30
forum: Programming Talk
---

### Post by tht00 on 2006-05-30
I'm looking for an add-on library where I can draw primitives (lines, circles, etc).  I found [SDL_gfx]("http://www.ferzkopp.net/Software/SDL_gfx-2.0/"), but I haven't been able to get it working.

Are there any others with better documentation?  Or, has anyone installed SDL_gfx before?

Thanks, 
Tom

---

### Post by tht00 on 2006-05-31
*bump*

---

### Post by Zdravko on 2006-05-31
No, but I have the same problem as you. I need a simple 2d graphic library for some simulation results. So far, OpenGl is the best documented API. Unfortunately it doesn't support primitives like circles - that is, the programmer must supply a function that handles the drawing of some shapes, even if they appear "primitive".

---

### Post by tht00 on 2006-05-31
[QUOTE=Zdravko]No, but I have the same problem as you. I need a simple 2d graphic library for some simulation results. So far, OpenGl is the best documented API. Unfortunately it doesn't support primitives like circles - that is, the programmer must supply a function that handles the drawing of some shapes, even if they appear "primitive".[/QUOTE]

I like what I saw with SDL_gfx, though, there is very little documentation (besides some demos they put in a RPM).  I got the demo binaries to run, but couldn't even compile them from source.

I'm really suprised SDL didn't have a 'primitive' library set already included.  I really don't want to write my own using putpixel(), or whatever it is. :-k

---

