---
title: "pygtk - window won't exit"
date: 2009-02-25
forum: Programming Talk
---

### Post by tbastian on 2009-02-25
I'm learning pygtk (I'm not using glade or any other graphical GUI creators) and I'm trying to make a popup window exit when the 'ok' button is pressed, however, when I press the button, the window just freezes up and doesn't exit. I can hit the 'x' button and have the window close nicely though...

I have tried using a dialog and I get the same result.

any ideas?

I'll attach my code.

---

### Post by tbastian on 2009-02-25
I have since posting this last message realised that my problem wasn't my code, but for some reason, running it using Idle caused my problem, and that using command line python made it work.

does anybody know what the issue is?

---

### Post by stevescripts on 2009-02-25
SWAG - Tkinter and gtk fighting over the event loop ...

---

