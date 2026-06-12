---
title: "QT button with a picture that can be grayed out?"
date: 2010-02-02
forum: Programming Talk
---

### Post by Zorgoth on 2010-02-02
I am making a GUI in QT.  This is my second QT project; my first was a simple 2D graphing program.  I am very new to it and the grapher was made a long time ago so I forgot a lot since then.  For now I want to be able to make a square button with a picture of my choice on top of it and with the option to "grey it out" when necessary so it can't be pressed.  How can I do that?

---

### Post by daasdingo on 2010-02-02
use a QToolButton to get a square button
and use setEnabled(bool) to grey it out

---

### Post by Zorgoth on 2010-02-02
Thanks!

---

