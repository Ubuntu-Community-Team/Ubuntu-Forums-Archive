---
title: "[SOLVED] How do I find motion of the mouse wheel on SDL?"
date: 2007-12-28
forum: Programming Talk
---

### Post by Fixman on 2007-12-28
I found that there is no event concerning the motion (not pressing) of the mouse wheel. How can this be achieved?

---

### Post by kdub432 on 2007-12-28
run 

$ xev 

and move your mouse wheel in the window and scroll. If nothing shows up, you will probably have to get a custom device driver for your particular mouse. If scrolling wheel produces output, your X server is not mapping your scroll wheel to the scroll command, a much simpler problem

---

### Post by Wybiral on 2007-12-28
The event is processed exactly like SDL handles mouse buttons (the event.type will be SDL_MOUSEBUTTONDOWN and SDL_MOUSEBUTTONUP), the codes (event.button.button) are: SDL_BUTTON_WHEELUP and SDL_BUTTON_WHEELDOWN

---

### Post by Fixman on 2007-12-28
> **Wybiral said:**
> The event is processed exactly like SDL handles mouse buttons (the event.type will be SDL_MOUSEBUTTONDOWN and SDL_MOUSEBUTTONUP), the codes (event.button.button) are: SDL_BUTTON_WHEELUP and SDL_BUTTON_WHEELDOWN

Thanks a lot.

---

