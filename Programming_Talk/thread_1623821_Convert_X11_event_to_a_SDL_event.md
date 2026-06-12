---
title: "Convert X11 event to a SDL event"
date: 2010-11-17
forum: Programming Talk
---

### Post by dosh on 2010-11-17
I have created X11 window and then attached(?) the window to SDL using "SDL_WINDOWID=%ld", windowid - Hack, And now am trying to access the events via SDL. Is there a way to convert the X11 event queue to a SDL queue? Or do I have to check the X11 events individually and send them individually to the SDL queue?

---

### Post by dwhitney67 on 2010-11-17
What do you mean by "X11" window?  Do you mean X/Motif (or Lesstif)?

All windows, regardless of the GUI library used to develop them, are displayed using X11 as the backbone.

I cannot fathom why you would attempt to blend two distinct GUI libraries for a particular project.  Could you not do everything using SDL?

---

### Post by dosh on 2010-11-17
OK to fill you in SDL lacks the ability in version 1.2 to do shaped windows, it is being looked at in 1.3 though. However X11 programming does have that ability. So that is why I want to blend two distinct GUI libraries. I like SDL's ease over X11.

---

