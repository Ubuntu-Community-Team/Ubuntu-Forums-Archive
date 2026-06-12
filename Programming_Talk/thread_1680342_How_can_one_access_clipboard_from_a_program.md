---
title: "How can one access clipboard from a program?"
date: 2011-02-02
forum: Programming Talk
---

### Post by TheHimself on 2011-02-02
It seems that I can't find the answer in libc or GTK documentation. I'd like an answer which doesn't depend on the desktop used.

---

### Post by cgroza on 2011-02-02
This is only useful when programming a GUI program, so I know that every GUI toolkit will offer some classes to access the clipboard. In wxPython for example, this is done in a similar way as in opening a file, drop the text and close it back.

---

### Post by TheHimself on 2011-02-03
I use GTK but it doesn't seem to have such a thing even though it supports in-application clipboards. I want to be able to access the system (X?) clipboard.

---

### Post by nvteighen on 2011-02-03
> **TheHimself said:**
> I use GTK but it doesn't seem to have such a thing even though it supports in-application clipboards. I want to be able to access the system (X?) clipboard.

There's no such thing as a system-wide clipboard. The closest thing I've seen is the KDE desktop-wide clipboard, but that's only for KDE, GNOME doesn't have that and I don't think the GTK+ API can communicate to the KDE clipboard.

---

### Post by TheHimself on 2011-02-03
But you can "copy" text in one application and paste it in another one. This means that there is a clipboard which is independent of individual applications. Doesn't? I think it has to do with X but as I browse the X library docs I can't find what I'm looking for.

---

### Post by TheHimself on 2011-02-06
I found the answer in the following function: 

gtk_clipboard_get_for_display ()

---

