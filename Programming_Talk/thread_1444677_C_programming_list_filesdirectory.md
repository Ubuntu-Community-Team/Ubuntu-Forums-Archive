---
title: "C programming list files/directory"
date: 2010-04-01
forum: Programming Talk
---

### Post by napz on 2010-04-01
hihi, how can i list all the files/ directory in a removable drive in C? something like a tree structure. i tried to open the /dev/sdb1 file and read its contents but i cant read anything from it?

please help me thanks

---

### Post by MadCow108 on 2010-04-01
use opendir, readdir, closedir etc recursively
there should be tons of examples to find with google

also you have to mount the drive to some folder before you can read it, e.g. sudo mount /dev/sdb1 /media/usb

---

### Post by Cracauer on 2010-04-01
Recursion kinda works but is clunky since you do everything on your own. Just think of controlling whether you follow symbolic links or not.

In the *BSD systems we have the fts(3) library, which does exactly the recursive iteration that you want. I am sure you can find a port to it in whatever Linux you use.

Failing that, I could use popen("find . -some -thing -or -other", "r");

Just be sure to not ignore error handling.

---

