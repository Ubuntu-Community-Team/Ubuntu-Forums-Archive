---
title: "app icons?"
date: 2007-11-25
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-11-25
this is another noob question:

I am currently trying develop in C++ under ubuntu. And I noticed something. That the executables don't have icons. What I mean is this:

In Windows an .exe usually is represented by an icon in Explorer.
In Ubuntu an executable doesn't have it's own icon in Nautilus.

Is this the way Linux "works"? Or is it possible to do that? (links plz)

thank you for your time.

---

### Post by jnorthr on 2007-11-25
can you right-click on an .exe to bring up a menu of options. There should be one there for icons you can choose to associate with the .exe. Alternatively create a link on the desktop pointing to the exe, then change the icon for the LINK.

---

### Post by Quikee on 2007-11-25
Icons for linux executables are separate - in ubuntu they are located in "/usr/share/pixmaps/" and/or "/usr/share/icons/<theme>/<size>/apps" if a theme wants to define its own icon.

---

### Post by SledgeHammer_999 on 2007-11-25
I don't if we are talking about the same thing. I'll try to be more specific:

In Windows let's say that you have an program in this path:
"C:\app.exe". If you open explorer and navigate to "C:\" you will see the app.exe represented by it's icon.

In Linux if you have the program in: "/home/<username>/Desktop/app" and open nautilus and navigate to "/home/<username>/Desktop/" your "app" won't be displayed by it's "own" icon, but by a generic one(used for all executables).

So my question is: Is it possible for programs to be represented by their own icons in Linux?

---

### Post by AlexThomson_NZ on 2007-11-25
Yep it is possible.  I use glade for most of my development, and when creating the main window, you can just point to a graphic to use for an icon (I make my own SVG icons).

Sorry, I don't know off the top of my head how to do it without Glade, but I suspect you can pass it as an argument when creating the window somehow.

This will need to be done at compile time though- don't think you can just 'add' an icon to an existing app and expect it to work

---

### Post by Awalton on 2007-11-25
> **SledgeHammer_999 said:**
> I don't if we are talking about the same thing. I'll try to be more specific:

In Windows let's say that you have an program in this path:
"C:\app.exe". If you open explorer and navigate to "C:\" you will see the app.exe represented by it's icon.

This is because Windows executables embed their icons directly within the executable file. This is technically possible in Linux, but is generally not done (same with most every other UNIX in the universe). Instead, applications in Ubuntu store their icons in a common location (/usr/share/pixmap/).

However, if you want an application in a directory to show a given icon, you can do so by making a .desktop file for that application, and specifying the pixmap to use (be it an SVG, PNG, etc). Google "desktop entry file" (or go here: [http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html](http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html) ) and you'll find what you're looking for.

---

### Post by SledgeHammer_999 on 2007-11-26
> **Awalton said:**
> This is because Windows executables embed their icons directly within the executable file. This is technically possible in Linux, but is generally not done (same with most every other UNIX in the universe). Instead, applications in Ubuntu store their icons in a common location (/usr/share/pixmap/).

However, if you want an application in a directory to show a given icon, you can do so by making a .desktop file for that application, and specifying the pixmap to use (be it an SVG, PNG, etc). Google "desktop entry file" (or go here: [http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html](http://www.gnome.org/learn/admin-guide/latest/menustructure-desktopentry.html) ) and you'll find what you're looking for.

That's what I want. I want to embed the icon and make nautilus use that to display my "app file".

---

