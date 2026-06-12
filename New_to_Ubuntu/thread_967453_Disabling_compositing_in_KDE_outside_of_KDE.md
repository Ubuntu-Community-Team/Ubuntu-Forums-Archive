---
title: "Disabling compositing in KDE outside of KDE?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Anonono on 2008-11-02
When I first installed KDE 4 into Ubuntu Hardy, I played around with it, and (stupidly) enabled compositing and desktop effects. Because my computer can't handle it, the windows just showed up as white, and everything else was black (The mouse was fine).
How can I disable it from outside of KDE?

---

### Post by Anonono on 2008-11-02
Bump.

---

### Post by Anonono on 2008-11-02
Anyone? I need answers fast.

---

### Post by Anonono on 2008-11-02
Come on, guys.

---

### Post by daverich on 2008-11-02
type metacity --replace


try to open a terminal with KDE somehow (if you have a terminal icon on your desktop you should be able to figure out where it is)

and type metacity --replace


Kind regards

Dave Rich

---

### Post by daverich on 2008-11-02
ok booted into KDE and figured it out.

Right-click on the desktop

the top entry in the menu is RUN COMMAND - you might not be able to see it but it should still work.

Click on the top of the menu to open RUN COMMAND and then type metacity --replace

should work but might take a few goes to click the right bit :)

Kind regards

Dave Rich

---

### Post by daverich on 2008-11-02
oh just noticed you're running it under hardy,- I'm running Ibex,- hopefully that menu is there for you :)

---

### Post by fooman on 2008-11-02
if you can't do anything in kde,  then boot into gnome,  open your home directory and in nautilus's toolbar click view and put a check next to "show hidden files"

find ".kde",  right click on it and choose "move to trash".  that should reset kde to the default configuration.

try and boot into kde and see if it works (may take a minute to rewrite the file so be patient).

hope that helps.

---

### Post by Anonono on 2008-11-02
> **fooman said:**
> if you can't do anything in kde,  then boot into gnome,  open your home directory and in nautilus's toolbar click view and put a check next to "show hidden files"

find ".kde",  right click on it and choose "move to trash".  that should reset kde to the default configuration.

try and boot into kde and see if it works (may take a minute to rewrite the file so be patient).

hope that helps.
That didn't do anything, and I can't do any of the other options because I can't see a thing under KDE.

---

### Post by daverich on 2008-11-02
> **Anonono said:**
> That didn't do anything, and I can't do any of the other options because I can't see a thing under KDE.

you dont need to see

Once KDE has finished booting:-

just right click, move the mouse down a very small amount and click.

then type metacity --replace and press enter.

Kind regards

Dave Rich

---

### Post by Anonono on 2008-11-02
> **daverich said:**
> you dont need to see

Once KDE has finished booting:-

just right click, move the mouse down a very small amount and click.

then type metacity --replace and press enter.

Kind regards

Dave Rich
Wow, that actually worked. Thanks! How can I restore the usual KDE window bar?

---

