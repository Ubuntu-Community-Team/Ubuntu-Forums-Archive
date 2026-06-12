---
title: "Saving code folds"
date: 2010-01-29
forum: Programming Talk
---

### Post by xtheunknown0 on 2010-01-29
I've written a C program using vim and created code folds. When I type :mkview, I get the following:

E739: Cannot create directory: /home/Not root/.vim/view
E190: Cannot open "home/Not root/.vim/view/=+cygdrive=+c=+Documents and Settings=+Not root=+My Documents=+informatics=+ele=+ele.c=" for writing.

How do I eradicate this problem?

TIA,
Albert

---

### Post by falconindy on 2010-01-29
[This page](http://www.linux.com/archive/feature/114138) has some good info about saving code folds in Vim.

---

### Post by Xnyper on 2010-12-12
I had the same problem, it looks like you need to create the directory:

~/.vim/view

After that everything is peachy.

---

