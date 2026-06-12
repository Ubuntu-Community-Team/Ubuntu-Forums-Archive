---
title: "Qt-Creator"
date: 2009-12-27
forum: Programming Talk
---

### Post by Woody1987 on 2009-12-27
I have an application which i am developing using Qt-Creator. I am currently on Ubuntu and when i compile the program and then run it, all the widgets looks like GTK but i want them to look like Qt. This isnt a problem on Kubuntu, only on ubuntu, obviously its because ubuntu use gnome, not kde. How do i keep the native Qt look?

---

### Post by OutOfReach on 2009-12-27
Well, your program IS using Qt, it's just using a theme that makes it look like GTK. (or does it let GTK render the widgets? I can't remember) It does this to make everything look more unified.

But if you want to change the style (theme) of all Qt applications, just install the qt4-qtconfig package and run the qtconfig-qt4 and change the theme.

---

### Post by Woody1987 on 2009-12-29
I installed qt4-qtconfig and i can change the style of qt but the kde4 oxygen style is not listed. How do i get it? Also, how do some qt applications like amarok display the oxygen style despite alternatives being selected in qt4-qtconfig.

---

### Post by OutOfReach on 2009-12-29
Hmmm, actually I'm not quite too sure the exact package where the Oxygen theme is kept. My guess is that it's included in one of the KDE packages.

Amarok, I __believe__, uses settings from KDE, not qt4-qtconfig. So to change the theme in Amarok, you'd have to change it from the KDE settings dialog.

I hope I am not being too confusing here, and I hope this helps.

---

### Post by Woody1987 on 2009-12-29
got it working, i installed systemsettings and oxygen appeared in qt4-qtconfig.

---

