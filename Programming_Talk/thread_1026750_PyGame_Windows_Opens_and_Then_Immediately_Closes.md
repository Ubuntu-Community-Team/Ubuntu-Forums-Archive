---
title: "PyGame Windows Opens and Then Immediately Closes"
date: 2008-12-31
forum: Programming Talk
---

### Post by cmkrause on 2008-12-31
Just as it sounds, I am opening the window with:
```
pygame.display.flip()
```
However whenever I run the script from the commandline like:
```
python testrastdraw.py
```
The window draws itself but then immediately closes.  Any ideas of what I am doing wrong.  Would it help if I uploaded more code?

Thanks!

---

### Post by skullmunky on 2009-01-03
Yes, upload more code.

Make sure you have an application loop of some kind; otherwise it certainly will just open the window and then quit.

---

