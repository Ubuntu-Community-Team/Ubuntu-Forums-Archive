---
title: "Gtk::Window* cannot be closed, Help!"
date: 2011-12-06
forum: Programming Talk
---

### Post by wisuzu on 2011-12-06
Why could be the causes of a window cannot be closed? 

I got a couple of misfuntion windows, they cannot be closed while the dialog whose create is still opened. Once the dialog whose opened that windows is closed, them can be closed normally ... is a strage behaviour.

In another version of the application i was creating the windows in the same way, but from the main window but now they cannot be closed. 

The main window is created in the main, the dialog is created in the main window and finally the two windows whose cannot be closed are created in the dialog.

Any hint/clue/fix would be appreciate! I can post the code if is needed. Thx in advance ;)

---

### Post by Petrolea on 2011-12-06
You don't handle the 'destroy' signal which gets emitted when you close the window. Bind it to gtk_main_quit() function (or a custom function that exists a program).

---

### Post by CoffeeRain on 2011-12-07
Petrolea, I have to say, your signature gets me every time. :D

---

