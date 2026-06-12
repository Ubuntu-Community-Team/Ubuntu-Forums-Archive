---
title: "Using the FTLK GUI toolkit?"
date: 2008-06-07
forum: Programming Talk
---

### Post by techmarks on 2008-06-07
Seems there are at least 3 incompatible versions of it, odd.

I've been using GTK+, but was interested in FLTK since it attempts to be a lighter toolkit.


Has any one used it? What do you think of it? Would you recommend it?

---

### Post by smartbei on 2008-06-07
I have used it, and it is easy enough, but its is also rather ugly (somewhat reminiscent of Tkinter). If you need to get something out quickly and simply, go ahead and use it - that was what I needed it for. If, however, you are going for something that you want more options for customizability and/or want it to look good/native, then go for wxWidgets (or, depending on the target platform) gtk or QT.

---

### Post by kknd on 2008-06-07
For general purpose applications, I prefer GTK due to l10n (bidirectional text and etc), nice look and good set of widgets. 

FTLK is great too, but I wouldn't use it unless I had very specific requirements.

---

### Post by smartbei on 2008-06-07
That's true, I forgot - FLTK does not support Unicode, which for me is a necessity for nearly all projects. What is the application you are building?

---

