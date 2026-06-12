---
title: "Devilspie problem"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-28
Hi, all:

I'm trying to get my KAlarm dialog windows to size properly.  Here's the contents of my kalarm.ds:

(if
  (contains (window_name) "KAlarm")
    (begin
      (wintype "normal")
      (geometry "700x700")
    )
)

The main KAlarm window sizes to 700x700, but the dialog window entitled "New Display Alarm - KAlarm" (when I try to create a new alarm) is too big, and jumps around on the screen when I try to click on it.  I'm informed that because the new alarm window is a dialog window, that you have to set the window type to normal so that devilspie can place it.  What am I doing wrong here?

---

### Post by tarahmarie on 2008-12-02
bump

---

### Post by tarahmarie on 2008-12-10
bump bump

---

