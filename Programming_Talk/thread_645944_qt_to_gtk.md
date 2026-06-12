---
title: "qt to gtk"
date: 2007-12-20
forum: Programming Talk
---

### Post by digitalis_vulgaris on 2007-12-20
I start project for development of Open Source Prepress Package. Idea is to use Scribus (C++, QT). Main distro for application should be Ubuntu, so it would be nice if we could migrate from qt to gtk. Is there some tool which automaticly convert qt to gtk?

---

### Post by Jessehk on 2007-12-20
I highly, highly doubt it. :)

---

### Post by samjh on 2007-12-20
No there isn't.

You have to understand that QT is much more than just a GUI toolkit, whereas GTK only serves as a GUI toolkit and nothing more.

QT incorporates databases, threading, networking, fonts, scripting, unit testing, and other functionality not related to GUIs.  Scribus probably uses some of them.

Also, there is nothing to stop using a QT application on Ubuntu.  Ubuntu even has its own KDE branch, Kubuntu.

---

### Post by digitalis_vulgaris on 2007-12-21
Thanks for the answers. I presume this will be the answer, but I have to ask.

---

