---
title: "What does CTRL-ALT-SHIFT-F12 do?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Stefanie on 2008-09-06
I wanted to assign a shortcut to CTRL-ALT-SHIFT-F12 and immediately after hitting the keys my screen went black with a blinking cursor in the top left corner. I had to use ALT-PrntScrn-REISUB to reboot my computer (Ubuntu Hardy) :-( What happened?

---

### Post by The Cog on 2008-09-06
The shift key was irrelevant. Ctrl-Alt-F1 through Ctrl-Alt-F6 give you six text TTY terminals. Ctl-Alt-F7 gives you the GUI TTY, and the higher F keys give you unused terminals. So all you had to do was Ctrl-Alt-F7 to get back. 

Actually, in the text-mode terminals, Alt-F7 will do - you don't need the Ctrl.

---

### Post by Stefanie on 2008-09-06
> **The Cog said:**
> The shift key was irrelevant. Ctrl-Alt-F1 through Ctrl-Alt-F6 give you six text TTY terminals. Ctl-Alt-F7 gives you the GUI TTY, and the higher F keys give you unused terminals. So all you had to do was Ctrl-Alt-F7 to gt back. 

Actually, in the text-mode terminals, Alt-F7 will do - you don't need the Alt.

Ok, thanks. I didn't have a clue, I didn't know that Ctrl-Alt-F7 would get me back and I wouldn't have guessed it...

---

### Post by MountainX on 2009-12-25
> **The Cog said:**
> The shift key was irrelevant. 

Maybe not. If compositing is enabled ALT-SHIFT-F12 toggles compositing. This can be very handy if a laptop doesn't properly resume from being suspended, as I just found out.

---

### Post by mozkill on 2010-12-06
Is there a guide available that shows all the Ctrl-Alt combinations possible with X-windows?

---

