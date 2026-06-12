---
title: "[SOLVED] Can't Open Applications Menu!"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by seuzy13 on 2008-06-21
The other day I went into my menu editor and unchecked some icons that had been placed there through wine, but were never removed when I uninstalled them. When I next tried to open the Applications menu, it wouldn't. It highlighted like it was opening and perhaps there was nothing in it. The Places and System menu are fine. What can I do?

EDIT--Also, I checked my /usr/share/applications menu. Everything appears to be there.
cat wine-winecfg.desktop
Everything appeared to be intact in the file as well.

EDIT2--
cat /usr/share/applications/gaim.desktop
cat: /usr/share/applications/gaim.desktop: No such file or directory
I saw a reference to this while reading [this article]("http://ubuntuforums.org/showthread.php?t=225390"). Could this be the problem or no? I was hoping that this article could help me in any case, but it assumes you have *some* kind of access to the applications menu, which I don't.

---

### Post by seuzy13 on 2008-06-21
I was actually able to solve the problem myself thanks to [this thread](http://ohioloco.ubuntuforums.org/showthread.php?p=3949738).

---

