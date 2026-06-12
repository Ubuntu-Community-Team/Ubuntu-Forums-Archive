---
title: "[SOLVED] black outline when minimizing a window"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by anonymous_user on 2008-11-16
When I minimize a window, there is this black outline of the window that shrinks to the window list. Is there a way to disable that?

---

### Post by FreewheelinFrank on 2008-11-16
If you have a suitable graphics card, you can enable visual effects:

System>Preferences>Appearance>Visual Effects.

Windows then shrink without frames appearing, and you have the option to select effects via the CompizConfig Settings Manager.

---

### Post by anonymous_user on 2008-11-16
Any other ways?

---

### Post by FreewheelinFrank on 2008-11-16
Not that I know of.

---

### Post by CatKiller on 2008-11-16
Press **Alt-F2** and run **gconf-editor**. Find the *apps/panel/global/enable_animations* key and disable it. That should (IIRC) stop them.

---

### Post by anonymous_user on 2008-11-16
Well I found how to disable it:

I opened gconf-editor and went to */apps/metacity/general* and checked *reduced_resources*.

---

### Post by metallicamike on 2008-11-16
you should mark this as solved then :)

---

