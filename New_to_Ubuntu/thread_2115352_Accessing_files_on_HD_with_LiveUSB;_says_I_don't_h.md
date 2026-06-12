---
title: "Accessing files on HD with LiveUSB; says I don't have permission"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by diablo75 on 2013-02-12
I have an old IBM Laptop I put Ubuntu on for someone else which has a failing hard drive (it's just started to throw out SMART alerts).  When attempting to boot normally it goes to a black screen with a cursor and no further after the boot splash has been up.  I've not tried recovery mode but feel confident I could get to a root CLI if necessary.  Preferably I'd like to use a LiveUSB to open their home folder and drag-n-drop the necessary files to backup before replacing the hard drive.  Unfortunately some of these files say I don't have permission to access them when trying to copy them to an external hard drive.

I know the username and password for their account.  Is there a way for me to tell the Live environment to open internal hard drive as if I were that user using their username and password?

---

### Post by Bashing-om on 2013-02-12
diablo75; Hi !

Have you tried:
```
gksudo nautilus
```from the liveCD terminal ?
I would expect to be able to drag and drop any files now.
[INDENT][INDENT]hth

[/INDENT][/INDENT]

---

### Post by diablo75 on 2013-02-12
Oh of course!  Why didn't I think of that. :confused:  I'm pretty certain that will do the trick, thanks for your helpful reminder :)

---

### Post by Bashing-om on 2013-02-12
diablo75;

There are those times that it is tough to see the forest for the trees.

---

