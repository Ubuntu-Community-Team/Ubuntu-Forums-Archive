---
title: "fsplit.c help"
date: 2010-04-05
forum: Programming Talk
---

### Post by mwparis on 2010-04-05
Code that previously worked under Ubuntu 9.10 (karmic) is not now.

[INDENT]mparis@assa79:~/SAID/said/lib$ ./fsplit ./junk.f
-bash: ./fsplit: No such file or directory
[/INDENT]

First question is: is this telling me that bash is running fsplit and that the executable fsplit can't find the file "./junk.f"?

Here's the directory listing:

[INDENT]$ ll
total 328K
-rwxr-xr-x 1 mparis mparis  12K 2006-08-11 10:51 fsplit
-rw-r--r-- 1 mparis mparis 9.7K 2006-08-11 10:51 fsplit.c
-rw-r--r-- 1 mparis mparis  29K 2010-04-05 12:43 junk.f
-rw-r--r-- 1 mparis mparis 146K 2010-03-22 11:24 libxzl.for-100322-tmp
-rwxr--r-- 1 mparis mparis  159 2010-01-14 14:31 mklib
-rwxr--r-- 1 mparis mparis  151 2010-03-23 23:58 mklib90
-rw-r--r-- 1 mparis mparis  52K 2010-01-22 14:40 nm.out
-rw-r--r-- 1 mparis mparis  52K 2010-01-22 14:40 nm.out2
[/INDENT]

---

### Post by gmargo on 2010-04-05
Bash is not running "fsplit".  That's what you'll see if your "fsplit" binary is a old executable format (a.out I believe [http://en.wikipedia.org/wiki/A.out](http://en.wikipedia.org/wiki/A.out)) or for another architecture.  Do a "file fsplit" to see what it says.  Fix it by recompiling fsplit.c.

---

### Post by mwparis on 2010-04-05
Yes -- that's exactly what it is. It needed to be recompiled as a 64-bit executable.

Thanks for the 'file' tip -- after all these years on *nix...sigh.

---

