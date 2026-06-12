---
title: "Library(ies) to access clipboard / accept drag and drop."
date: 2008-06-20
forum: Programming Talk
---

### Post by Vadi on 2008-06-20
Asking this for someone else, but how would one in C++ be able to write to the system clipboard?

Also, accept drag and drop into an SDL window?

---

### Post by smartbei on 2008-06-21
The simplest way I know of to do this is to use the xsel. First install it from the repos, and then you can run it as a child process and that as a file object ... See its help.

You can also do this with gtk as well - see the clipboard_get function I believe.

Drag & Drop I am not so sure about.

---

### Post by Vadi on 2008-06-21
Yeah, I know how to do the clipboard and drag & drop in gtk, but not in sdl. I'll look at xsel.

Does anyone know how to accept drag and drop with sdl though?

---

