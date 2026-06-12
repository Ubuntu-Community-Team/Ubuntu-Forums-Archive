---
title: "opengl windows leave behind artifact when moved"
date: 2009-12-08
forum: Programming Talk
---

### Post by Ultros88 on 2009-12-08
Hi, I've been running some basic tests programming opengl in c++. Recently I've tried using both SDL and FLTK to provide an opengl window. SDL works fine... except when I move the window, vestiges of the opengl display remain in their previous location. FLTK has this same problem, in addition to the fact that it will often clear out the opengl drawing either when the program is first run or when the main window is moved or resized. I would greatly appreciate it if someone could help me resolve these issues, thanks! -Ultros

---

### Post by Zugzwang on 2009-12-08
Does the problem vanish if you switch of the desktop graphic effects (Systems->Settings->Appearance, last tab)? If yes, this is a problem with the window manager and shouldn't be of your concern.

---

### Post by Ultros88 on 2009-12-08
Thanks, that fixes the most glaring problem. The opengl content is no longer left behind, so to speak. However, on moving the window there is now an artefact consisting of a greyed out frame that lags slightly in its disappearance. I'm guessing this is another issue with the window manager that I should not be concerned about. Do you think there is any reason to report this as a bug, if it hasn't been already?

Cheers

---

### Post by Zugzwang on 2009-12-10
> **Ultros88 said:**
> Thanks, that fixes the most glaring problem. The opengl content is no longer left behind, so to speak. However, on moving the window there is now an artefact consisting of a greyed out frame that lags slightly in its disappearance. I'm guessing this is another issue with the window manager that I should not be concerned about. Do you think there is any reason to report this as a bug, if it hasn't been already?

Cheers

Uuuh, good question. I have to admit that I have no clue. Maybe someone else can say something about it?

---

