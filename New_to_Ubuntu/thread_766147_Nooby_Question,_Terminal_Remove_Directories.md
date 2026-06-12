---
title: "Nooby Question, Terminal: Remove Directories"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Sugi on 2008-04-25
How in h.e.double hacky sticks do I remove directories with files and other folders in it?

For Example:
I want to delete this directories called pancakes.  How do I do it?

/pancakes/
includes
/pancakes/tasty pancakes/best kind of pancakes/its true.txt
/pancakes/not so tasty pancakes/i dont like these kind of pancakes.txt
/pancakes/the last thing from tasty pancakes/nothing.txt

rm /home/usr/pancakes/
rmdir /home/usr/pancakes/
rm /home/usr/pancakes/*
rmdir /home/usr/pancakes/*
sudo rm /home/usr/pancakes/*
sudo rmdir /home/usr/pancakes/*

The terminal has something like "Can Not delete directory".  So, what do I do?

Thank you,
Sugi

---

### Post by amingv on 2008-04-25
You can do:
```
rm -rf pancakes
```

Just remember to put the cap back up in the syrup after you do so :).

---

### Post by ahaurw01 on 2008-04-25
Hi Sugi

use
```
rm -r <directory name>
```
to recursively delete files inside that directory and the directory itself.
it'll prompt you if you're deleting some protected files or anything out of the ordinary.
-aaron

---

### Post by Sugi on 2008-04-25
> Just remember to put the cap back up in the syrup after you do so

Ha ha, I didn't get that right away.  I just kept reading "just remember to put the cap back up" and i thought to myself "caplock?  back up?  what????"

> to recursively delete files inside that directory and the directory itself.
it'll prompt you if you're deleting some protected files or anything out of the ordinary.
-aaron

I had to remove some stuff from a micro SD card and I couldn't remove the files from the GUI for some odd reason.  So instead of removing every directory I thought I would find a way to remove all directories and I even had that problem of the protected files, but sudo took care of everything else for me though.  

Thanks guys for the help. :)
Sugi

---

