---
title: "2D collision detection with SDL - how?"
date: 2006-02-02
forum: Programming Talk
---

### Post by Sslaxx on 2006-02-02
I'm looking for good pixel-level collision detection routines (or, failing that, pointers on how to write one!) for SDL (using C++). The big stumbling block is pixel access - how do I do this without having to write multiple routines depending upon the bitdepth of a surface?

---

### Post by scourge on 2006-02-03
Try this:
[http://gpwiki.org/index.php/C:Collision_Detection_between_2_SDL_Surfaces](http://gpwiki.org/index.php/C:Collision_Detection_between_2_SDL_Surfaces)

It's a very simple way to do it, but also quite expensive.

---

### Post by Sslaxx on 2006-02-03
[QUOTE=scourge]Try this:
[http://gpwiki.org/index.php/C:Collision_Detection_between_2_SDL_Surfaces](http://gpwiki.org/index.php/C:Collision_Detection_between_2_SDL_Surfaces)

It's a very simple way to do it, but also quite expensive.[/QUOTE]
Except it sucks, I've already attempted to get it to work - the attached code just doesn't work!

---

### Post by Keffin on 2006-02-03
Install this: [http://www.etek.chalmers.se/~e8cal1/sge/]("http://www.etek.chalmers.se/%7Ee8cal1/sge/")

It works with SDL, providing some very nice functions for things like pixel-perfect collision detection.

The functions that should interest you in particular are sge_make_cmap and sge_cmcheck. You should also use sge_destroy_cmap when you are done with the sge_cdata structures created by sge_make_cmap.

I have used it and it works very well for me.


EDIT: Sorry, I should have pointed out it is in the breezy universe repository as libsdl-sge-dev

---

### Post by Sslaxx on 2006-02-03
[QUOTE=Keffin]Install this: [http://www.etek.chalmers.se/~e8cal1/sge/]("http://www.etek.chalmers.se/%7Ee8cal1/sge/")

It works with SDL, providing some very nice functions for things like pixel-perfect collision detection.

The functions that should interest you in particular are sge_make_cmap and sge_cmcheck. You should also use sge_destroy_cmap when you are done with the sge_cdata structures created by sge_make_cmap.

I have used it and it works very well for me.

EDIT: Sorry, I should have pointed out it is in the breezy universe repository as libsdl-sge-dev[/QUOTE]
Keffin, checking it out now. Thanks for that! It looks interesting. Wonder if it can be compiled as a static library (to reduce dependency trouble)...

---

### Post by Keffin on 2006-02-03
[quote=Sslaxx]Keffin, checking it out now. Thanks for that! It looks interesting. Wonder if it can be compiled as a static library (to reduce dependency trouble)...[/quote]

As far as being technically possible I'm sure it is, as long as you don't mind compiling it yourself (after possibly fiddling with the Makefile). But it is GPL code so if you statically link it into your program and distribute it then your program must also be GPL (as I understand it). I can't see how the dependency causes any "trouble" though, as long as you point out that it is needed. I even got my program working on windows linking to the sge and sdl dll files.

Good luck.

---

### Post by Sslaxx on 2006-02-03
Not GPL, but *L*GPL, which should eliminate the need to worry about static/dynamic linking - not that I didn't plan on releasing the code I'm working on anyway (not that anybody'd seriously want it!) under the terms of the GPL.

---

### Post by malcolm81 on 2009-11-07
> **Sslaxx said:**
> Except it sucks, I've already attempted to get it to work - the attached code just doesn't work!

Yeah I had this problem too.  The headers/source files are c++, i.e. they use overloading and default values, but the extension is ".c".  I "fixed" it by eliminating the one default value in the header and commenting out the bounding box and the bounding circle code with ifdef, but if you needed those you'd have to mangle the function names.  I guess I knew most people programmed games in c++, but I didn't realize that it was so ubiquitous that an error like this in code attempting to be portable could slip through.

My problem is that after all of that the pixel collision only works if you are using a colorkey, and I guess I'm using an alpha channel (I just loaded up some PNG's with transparency using SDL_image.)

---

### Post by Sslaxx on 2009-11-09
Rise from the grave...

Managed to get a pixel-collision detection routine working, fixing up SDL_Collide.

---

