---
title: "I want to make a screensaver for Linux"
date: 2009-03-24
forum: Programming Talk
---

### Post by Volt9000 on 2009-03-24
The title of the thread says it all-- I'd like to write my own screensaver to use in Linux.

Programming is not an issue, as I have plenty of coding experience, but in a Windows environment. I don't mind learning a new language (looking for an excuse to give Python a go) but I really have no idea where to start, in a Linux environment.

I can write command-line stuff fine with C, but have no idea how to tackle a grahpics application, let alone a screensaver.

Can anyone point me in the right direction?

---

### Post by squaregoldfish on 2009-03-25
Never tried it myself, but the FAQ for XScreenSaver contains a hint or two. Try the file referenced [here]("http://www.jwz.org/xscreensaver/faq.html#writing-savers") for a start.

Steve.

---

### Post by Volt9000 on 2009-03-25
Ok so it seems that there's a difference between xscreensaver and gnome-screensaver. I presume the former is universal for all X, and the latter is written in GTK and specific to GDK, is this correct?

---

### Post by squaregoldfish on 2009-03-26
xscreensaver and gnome-screensaver are the control programs. The screensavers themselves are independent programs, and can be run as such. If you want to write a new saver, you just need to create the program to draw the pretty stuff!

Steve.

**EDIT:** On my system, all the screensavers are in /usr/lib/xscreensaver

---

