---
title: "Gtk on win32"
date: 2008-09-26
forum: Programming Talk
---

### Post by Emill on 2008-09-26
Hi. I have successfully compiled an .exe for windows with Gtk. The problem is: when I start the program, I see my GUI as expected, but also an empty command prompt. I don't want that. How to hide it?

---

### Post by Vadi on 2008-09-26
What do you mean by that?

Like a cmd terminal starts up?

---

### Post by Emill on 2008-09-26
Yep, besides the Gtk-window. I use gtkmm.

---

### Post by Vadi on 2008-09-26
Ahh. Not sure, I don't run into such an issue.

---

### Post by tanderson on 2008-09-27
Maybe this will help. Down towards the bottom in the section about the windows console.

[http://www.signal11.us/~alan/gtkmm_win32/gtkmm_windows.html](http://www.signal11.us/~alan/gtkmm_win32/gtkmm_windows.html)

---

### Post by Emill on 2008-09-27
Anybody who knows how to do it with MinGW/g++?

---

### Post by SeanHodges on 2008-09-27
I have no idea, but those instructions seem to suggest that you can send a "/SUBSYSTEM:WINDOWS" switch to the linker. Perhaps this works with GCC as well?

---

### Post by Vadi on 2008-09-27
Do you use an -mwindows flag in mingw makefile?

---

