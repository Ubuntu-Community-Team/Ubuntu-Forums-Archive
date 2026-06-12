---
title: "Fork an application to only change the name"
date: 2014-02-22
forum: Packaging and Compiling Programs
---

### Post by thebian on 2014-02-22
Hello,
i have a curiosity: i just red that Elementary team forked some applications to only change the names and apply some minor changes.

My question is: how, practically, i can change the name of an application? Sure, i'm not interested in change the name of the application and after say "hey this is my app", i just want to know how..

thanks for everyone that will help me!

---

### Post by tgalati4 on 2014-02-23
The MATE desktop did the same thing.  Every gnome program needed a new name so that it would not conflict with the same-named programs in gnome3.  That way, you can install MATE and gnome3 shell or Unity on the same system.  So *nautilus* (the file manager) is named *caja* in MATE.

I'm not sure how it is done exactly, but I would guess that the names are changed in the source code (a tedious process) and then recompiled.  Then when the program is packaged, the final name is given.

Though not recommended, you can change any program name in linux.  It might cause some breakage.

For instance the *which* command shows you where a program is located:

```
which firefox
```

It might look like:

tgalati4@Mint14-Extensa ~ $ which firefox
/usr/bin/firefox

Typically if you need a unique name for a program, you can create a script that launches the program with your particular customizations.  For instance, I had *firefast* which was *firefox* run completely from a ramdisk to improve speed.  So *firefox* and *firefast* both existed on the system.

---

### Post by thebian on 2014-02-23
And for example how i can do somethings like the change firefox --> firefast??

---

