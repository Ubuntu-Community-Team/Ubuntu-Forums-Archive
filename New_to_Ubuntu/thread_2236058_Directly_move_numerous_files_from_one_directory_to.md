---
title: "Directly move numerous files from one directory to another"
date: 2014-07-24
forum: New to Ubuntu
---

### Post by Johyn on 2014-07-24
Greetings all! :p

Could someone tell me how to move numerous files from one directory to another, meaning directly. Cause, well, when I select all the files, there's a 70% chance that they will be unselected with my left click to move them...

---

### Post by Dennis N on 2014-07-24
After selecting those to be moved, use Ctrl +X to cut, then switch to the destination directory window,  and Ctrl + V to paste. Together, these are the same as move.

---

### Post by slickymaster on 2014-07-24
In a terminal window```
mv /path/to/source/folder/* /path/to/target/folder/
```

If there are too many files in the source folder you might want to try something like:
```
cd /path/to/source/folder/
find -exec mv {} /path/to/target/folder/ +
```

---

### Post by Bucky Ball on 2014-07-24
I have changed the title of your thread to improve your chances. Good luck.

---

### Post by Johyn on 2014-07-24
Okokok, thxs for you! :p

---

