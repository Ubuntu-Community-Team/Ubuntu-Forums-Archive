---
title: "Quick SDL_image question (scaling)"
date: 2007-07-11
forum: Programming Talk
---

### Post by Sockerdrickan on 2007-07-11
Hi, how can I scale a 2560x1600 image to 1440x900(In the memory) in SDL before I draw it, thanks!
(I hope I can lol):)

---

### Post by slavik on 2007-07-11
personally, I would use OpenGL and have it scale automatically (not sure how to save it back though)

but if you are looking for algorithms, look up bicubic (with 4x4 samples, it is very comparative to lanczos)

---

### Post by Wybiral on 2007-07-12
SDL doesn't have any surface stretch/shrink built in... There may be a helper library for it somewhere (I think I seen a rotation one once).

OpenGL would certainly work... But may very well be overkill unless you could adapt your project to use it (it will require loading to an OpenGL texture and rendering).

If there are no SDL libraries for it, slavik may be correct in suggesting to do it algorithmically yourself.

---

