---
title: "The Difference Between X, GNOME, GTK+"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by azurepancake on 2008-06-06
I know that X, GNOME/KDE/Xfce, GTK+ etc. are all related to the GUI, but I am having trouble deciphering the main differences between them. I THINK I have a basic idea of there purposes. If anyone can clear it up for me I'll appreciate it.

Here is a short summarization of what I've gathered..

_**X Window System** (X11)_: 
X is the most abstract to me. It seems it's purpose is to serve as the core of the GUI and that it manages windows and such. It is "network transparent" meaning it can be used over a network..  
[U]
**GTK+ GIMP Tool Kit**[/U]:
I'm guessing this is simply a GUI developers tool kit. 

_**GNOME/KDE/Xfce**_:
I suppose these can be summarized as packages that offer free, GUI tools.

Again, if anyone can broaden my understanding of these or correct my assumptions, I will be ever grateful.

Thanks!

---

### Post by Paqman on 2008-06-06
Looks pretty good to me.

GTK is a set of ready-made bits and pieces that devs can use to build the GUIs for their apps. Instead of having to design all the little knicknacks that make up every window they can just use a standard set of components.

---

### Post by Trail on 2008-06-06
Pretty much.

X is a server-client system to display windows and other graphical entities; but it is not a window manager. Each desktop environment usually packs their own window manager (KDE uses kwin, GNOME uses metacity, there's also compiz etc).

GTK is not really a developers' tool kit; it is a set of functions (API - application programming interface) and instructions on how to paint graphical entities on screen (like windows, forms, buttons, combo-boxes, etc). It originated from GIMP and it's used byt GNOME. It is written in the C language. The KDE "equivalent" (loosely used here) would be QT.

Desktop Environments (KDE, GNOME, etc) are as you said packages closely tied together, trying to provide integrated, commonly themed applications etc.

Check wikipedia for detailed info.

---

