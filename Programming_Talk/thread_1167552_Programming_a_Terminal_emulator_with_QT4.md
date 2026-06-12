---
title: "Programming a Terminal emulator with QT4"
date: 2009-05-23
forum: Programming Talk
---

### Post by SadaraX on 2009-05-23
I am interested in writing a terminal emulator program, and hopefully using QT4 or GTK(+) to handle the basic GUI functions. I am having trouble finding any information on doing this.

All I really want is to run a shell (with vim or screen for example) in a QT4 or GTK(+) window. The important things are control over the display fonts and the background (image) underneath the displayed shell text. Konsole and Gnome-terminal lack the specific features I need. 

Can anyone recommend documentation, tutorials, libraries, or guides for doing this?

Edit: Before anyone asks: Yes I have explored the numerous terminal emulators available, such as konsole, gnome-terminal, etc. They don't give me what I need.

---

### Post by crdlb on 2009-05-23
I'm not a Qt guy, but I did a bit of googling and came across [http://qtermwidget.sourceforge.net](http://qtermwidget.sourceforge.net), which is a Qt4 terminal widget. I'm not sure where you're planning to go with this, but that code should at least be helpful as a guide.

From that page, it also seems that Konsole itself is embeddable, and it might be possible to make the modifications you want to it in that form (I have no idea).

---

