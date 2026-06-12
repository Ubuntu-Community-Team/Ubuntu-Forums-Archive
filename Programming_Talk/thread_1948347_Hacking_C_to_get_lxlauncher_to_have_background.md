---
title: "Hacking C to get lxlauncher to have background"
date: 2012-03-28
forum: Programming Talk
---

### Post by spiralciric on 2012-03-28
I downloaded lxlauncher latest version, compiled it, but it just cannot use any background image or be just transparent. I edited background_dir in src/lxlauncher.c, but that gave no results. Could anyone help me find how to do this? Instructions in Readme are offcourse not correct and outdated from the time it did not use cairo libs. Here is the source:
[http://sourceforge.net/projects/lxde/files/LXLauncher%20%28for%20Asus%20EeePC%29/LXLauncher%200.2.2/](http://sourceforge.net/projects/lxde/files/LXLauncher%20%28for%20Asus%20EeePC%29/LXLauncher%200.2.2/)

---

### Post by CynicRus on 2012-03-28
[http://sourceforge.net/tracker/index.php?func=detail&aid=2666710&group_id=180858&atid=894871](http://sourceforge.net/tracker/index.php?func=detail&aid=2666710&group_id=180858&atid=894871)

---

### Post by spiralciric on 2012-04-02
Thanks, will try it today.

---

### Post by spiralciric on 2012-04-03
I'm having some problems with patching (path is correct):
```
patch -p0 < lxlauncher-background.patch 
patching file lxlauncher/src/lxlauncher.c
Hunk #1 succeeded at 54 with fuzz 2 (offset 9 lines).
Hunk #2 FAILED at 230.
Hunk #3 FAILED at 249.
Hunk #4 FAILED at 281.
Hunk #5 FAILED at 574.
Hunk #6 FAILED at 623.
Hunk #7 FAILED at 659.
Hunk #8 FAILED at 666.
Hunk #9 FAILED at 676.
8 out of 9 hunks FAILED -- saving rejects to file lxlauncher/src/lxlauncher.c.rej
can't find file to patch at input line 147
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: menu-cache/libmenu-cache/menu-cache.c
|===================================================================
|--- menu-cache/libmenu-cache/menu-cache.c    (revision 1247)
|+++ menu-cache/libmenu-cache/menu-cache.c    (working copy)
--------------------------
File to patch: lxlauncher/src/lxlauncher.c
patching file lxlauncher/src/lxlauncher.c
Hunk #1 FAILED at 48.
Hunk #2 FAILED at 212.
Hunk #3 FAILED at 485.
Hunk #4 FAILED at 544.
4 out of 4 hunks FAILED -- saving rejects to file lxlauncher/src/lxlauncher.c.rej
can't find file to patch at input line 193
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: menu-cache/libmenu-cache/menu-cache.h
|===================================================================
|--- menu-cache/libmenu-cache/menu-cache.h    (revision 1247)
|+++ menu-cache/libmenu-cache/menu-cache.h    (working copy)
--------------------------
File to patch: 

```

---

### Post by spiralciric on 2012-04-03
Tried with p0 and p1, and none works.

---

