---
title: "[SOLVED] Splitscreen in SDL"
date: 2008-05-20
forum: Programming Talk
---

### Post by Zeotronic on 2008-05-20
C++/SDL/SDL_gfx: I'm working on a game that will have multiplayer splitscreen support... something I don't know about you, but I have rarely seen outside of consoles... but that is irellevent. **How could one go about splitscreen in SDL?** I had thought I was going to just draw the screens onto individual surfaces and apply them onto the main veiw... but even with only one screen rendered like that I brought my game up to using 50% of my processor (from 15-20%)... and that is unacceptable, because I'm designing my game with a much weaker platform in mind.

---

### Post by Zugzwang on 2008-05-21
You could clip against the borders of your "half screen" when drawing onto the screen. This way you wouldn't require any extra surfaces to draw onto.

---

### Post by slavik on 2008-05-21
look into using gl_Viewport().

---

### Post by Zeotronic on 2008-05-21
> look into using gl_Viewport().
You seem to be misunderstanding me... I am using SDL *itself* for rendering, not OpenGL, through SDL.
> You could clip against the borders of your "half screen" when drawing onto the screen. This way you wouldn't require any extra surfaces to draw onto.
But I would have to resize all of my various loaded images (to maintain similar view proportions), so I have to ask if this would really be faster than drawing onto a surface, which would instead, itself, need be resized. Putting it simply, **is drawing onto the screen faster than drawing onto a surface and then drawing it onto the screen?** And preferably a general estimate of how much so.

Edit:
In retrospect... my choice of words, simplistically, do not properly define the question.

---

### Post by Zugzwang on 2008-05-21
> **Zeotronic said:**
> But I would have to resize all of my various loaded images (to maintain similar view proportions), so I have to ask if this would really be faster than drawing onto a surface, which would instead, itself, need be resized. Putting it simply, **is drawing onto the screen faster than drawing onto a surface and then drawing it onto the screen?** And preferably a general estimate of how much so.


Ok, so your chain of drawing currently is the following:
```

Sprites/Background/Whatever -> Split screen buffer -> Primary surface

```

**For the case that you have a proper screen driver installed (which allows 2D/3D acceleration):**

This chain is extremly slow if the Sprites buffer is in the GFX card's memory, but the split screen buffer isn't. If everything is in the GFX card's memory, it shouldn't be too slow. However, in such cases scaling is usually very fast, so you could think about scaling your sprites/whatever to the correct proportions on-the-fly *while* drawing to the primary surface directly (the other approach). For more modern graphic cards (2000 or later), the speed of a surface copy almost only depends on the number of pixels written.

**For the case that there isn't a proper screen driver installed allowing surface copies by hardware**, things might be different. The last time I programmed SDL was on Windows, so this wasn't an issue there. No clue what's faster here.

---

