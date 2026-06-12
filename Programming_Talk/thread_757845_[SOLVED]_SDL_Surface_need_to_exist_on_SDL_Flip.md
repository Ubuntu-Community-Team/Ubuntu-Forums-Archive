---
title: "[SOLVED] SDL_Surface need to exist on SDL_Flip?"
date: 2008-04-17
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-17
C++/SDL: Recently I have had an error which crashes my application that I'm writing... I know it comes from the code I have written to draw text on the screen... the code applies the letter surfaces onto a line surface, which is applied onto a full text surface. All of the letters work on their own, and if I don't apply the full text surface to the screen the application doesn't crash. I was wondering if the surfaces applied to the screen have to exist when SDL_Flip is declared (because they dont... they cease existing shortly after they are applied)... I've been thinking about what could be going wrong for 2 days (not all of the time mind you) and this is the only thing I have came up with so far... when I try applying the line surfaces directly to the screen though, and ignore the full text surface, it doesn't crash either... though I cant see the text I put on the lines. (or, for that matter, the lines themselves) They too are deleted before SDL_Flip.

Does anyone have any idea?

---

### Post by Wybiral on 2008-04-17
What do you mean? Are you flipping a surface that doesn't exist?

---

### Post by Zeotronic on 2008-04-17
I'm sorry, I must not have been clear... I am flipping another surface which I referred to throughout my original post as 'the screen'... it *does* exist... throughout the program.

---

### Post by Wybiral on 2008-04-17
Oh, you mean you've blit'd some other surfaces and freed them, and you want to know if they need to exist when the main surface is flipped?

No, they don't. When you blit them, you are updating the pixel data of the main surface so it doesn't need them afterwards.

---

### Post by Zeotronic on 2008-04-17
Thats what I thought... hmm... I wonder what is causing my error then?

---

