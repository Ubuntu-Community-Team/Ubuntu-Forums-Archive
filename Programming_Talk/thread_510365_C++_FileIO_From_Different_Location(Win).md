---
title: "C++ File/IO From Different Location(Win)"
date: 2007-07-26
forum: Programming Talk
---

### Post by mgoblue on 2007-07-26
Hi, this is for windows (I know how to do it on Ubuntu, well kinda):

I'm writting a program that uses some file I/O to read and write data.  I'm also using QT for the GUI.  How would I be able to read and write files that are located in a different location from the .exe ? For example, the .exe is on the desktop and the input file would be in My Documents.

Thanks

---

### Post by Wybiral on 2007-07-26
Use the absolute location instead of the relative one.

---

### Post by mgoblue on 2007-07-26
> **Wybiral said:**
> Use the absolute location instead of the relative one.

By this do you mean when setting the file name set it like "c:\..." up to where it is located?

---

### Post by Wybiral on 2007-07-26
Yeah. How else do you expect it to know where it is?

You can go down to it if you want to use the relative path:

"../../../Desktop"

But if you know here the file is, just use the entire path (that way your executable will work from anywhere).

---

### Post by [h2o] on 2007-07-26
I am quite certain that there are Windows equivalents of $HOME environement variables that should take you in the right direction.

---

