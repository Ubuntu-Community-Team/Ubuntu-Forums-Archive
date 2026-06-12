---
title: "Seperating Gui platforms from functionality"
date: 2007-10-23
forum: Programming Talk
---

### Post by keifer on 2007-10-23
I guess this sort of parellels slavik's thread, but I was wondering how important it is to try and separate the actual functionality of a program away from the GUI platform.

For example: when using PyQt, I have access to both Qt's and Python's datatype implementations. Is it advisable to take full advantage of Qt through out the program, or should I try to limit my use of Qt strictly to the area of constructing and managing the UI?

Is it better practice to consistently use the same datatypes through out, or is it better to write code that keeps the core of the program platform agnostic? I find that it's easier for me to understand my code if I do the former, but the latter seems to promote better code reuse. Is this something there is a general consensus on?

---

### Post by Wybiral on 2007-10-23
If it's a serious application, then you may need to port it to GTK, or command line, or even Windows (it could happen...) so if you liter your code with interface specific code, you're doomed.

Also, sometime in the future QT might make some design changes that they may need to sacrifice some backward compatibility for (happens all the time). If you want to stay up-to-date, you'll have to hunt through all of your code to make those changes (sort-of like the print vs print() coming up in Python 3, except that's a pretty easy fix, GUIs are not) but if you keep it as confined as possible, updating will be smooth.

Not to mention the ease of unit testing / debugging / optimizing with modularized code. And if it's not a serious program you're working on, then it's practice for when you write a serious program, so do it right anyway! :)

---

### Post by slavik on 2007-10-23
you should try to NOT use QT/GTK(GDK) datatypes for stuff that has nothing to do with them.

For example, creating a listview in GTK requires you to user a liststore (which is part of GTK/Glib) so that's fine. But if you have something like a sorted list that you want to use that is part of QT, it's not a very good idea to use it, it would be better to use something like Boost. Even better would be to write your own (which is what I am about to do for my little project).

---

