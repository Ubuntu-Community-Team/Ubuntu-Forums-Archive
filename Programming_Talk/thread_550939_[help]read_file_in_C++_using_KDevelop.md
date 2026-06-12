---
title: "[help]read file in C++ using KDevelop"
date: 2007-09-14
forum: Programming Talk
---

### Post by silverhat on 2007-09-14
Hi there. When using Visual C++(in windows), if i want to read a file(e.g. text.txt), i put it in the same folder& use this code: ifstream in("text.txt");
But now, i'm using KDevelop, if i want to  do this, I must enter the full address of file :  ifstream in("/home/.../src/text.txt");
I don't like to enter the full address.
Everyone please help me solving this.Thanks!

---

### Post by nonewmsgs on 2007-09-14
~/ means /home/currentuser

so try "~/src/txt.txt"

edit another idea: set the path as a string maybe?  that might be more trouble than it's worth, i'm not sure.

---

### Post by silverhat on 2007-09-14
Thanks.I solved it.

---

### Post by nonewmsgs on 2007-09-14
what is the solution?

---

### Post by CptPicard on 2007-09-14
Just a hunch... does your KDevelop build the binary into some other directory than the source directory, where you keep the txt file? Because you *should* be able to find the file from the same directory without giving the complete path.

This is of course different if your build is not in the source dir. :)

---

