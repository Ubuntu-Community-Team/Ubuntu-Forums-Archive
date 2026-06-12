---
title: "Converting C++ Win32 API form console to GUI"
date: 2008-03-07
forum: Programming Talk
---

### Post by kool_kat_os on 2008-03-07
Ok...sorry for so many questions....

I have written a C++ app in win32 api that runs in the console...does anyone know any REAL GOOD tutorial on how to write it in a GUI interface? 

Thanks

EDIT: i spelled "from" wrong in the title.

---

### Post by deadimp on 2008-03-07
You'd probably have to learn a GUI API in general, something like Windows MFC if you're suicidal, GTK+ w/ gtkmm wrapper, Qt, wxWidgets, etc. Most of these APIs have various designers that you can use for them.
Drawing out a design would help, figuring what kind of controls you'd need, how to connect you're input to your output, or separate presentation logic from business logic in MVC, if you're big on patterns.

---

