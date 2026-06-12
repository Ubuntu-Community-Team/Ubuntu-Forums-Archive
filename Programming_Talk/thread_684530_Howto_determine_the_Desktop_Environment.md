---
title: "Howto determine the Desktop Environment"
date: 2008-02-01
forum: Programming Talk
---

### Post by quandary on 2008-02-01
Hi!

Question: From within a C/C++ program, how do i determine the Desktop Environment (that is to say: is it Gnome or KDE or XFCE, or another)?

---

### Post by quandary on 2008-02-01
bump

---

### Post by LaRoza on 2008-02-01
You can't really. There is another thread that looked at this issue in detail.

---

### Post by stroyan on 2008-02-01
This was discussed in thread [http://ubuntuforums.org/showthread.php?t=652320](http://ubuntuforums.org/showthread.php?t=652320)

The range of possibilities is just too complicated to get a simple answer.
The X properties approach that I pointed to in the other thread works pretty well.```
WM_WINDOW=$(xprop -root _NET_SUPPORTING_WM_CHECK);
WM_WINDOW=${WM_WINDOW##* };
WM_NAME=$(xprop -id $WM_WINDOW 8s _NET_WM_NAME)
WM_NAME=${WM_NAME##* };
echo $WM_NAME
``` But when the window manager is beryl or compiz that may not match the question that you really wanted answered.
That kind of leads to the underlying question-
    What does your program need to know about the environment that it can't react to with a portable standard mechanism?

---

### Post by quandary on 2008-02-01
Thanks. I think i will use the process list.

---

