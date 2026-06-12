---
title: "wxPython Menu Bar Problem"
date: 2010-11-27
forum: Programming Talk
---

### Post by pauljwells on 2010-11-27
I think there may be a bug in wxPython on Ubuntu?

I am writing an application in Python / wxPython. It runs fine on Windows and it runs fine from Eclipse on Ubuntu.

However, if I run it 'directly', either by double-clicking or from a $python filename.py command in terminal then the menubar is not displayed.

Everything else works, including the toolbar

Any ideas?

---

### Post by stani on 2010-12-04
> **pauljwells said:**
> I think there may be a bug in wxPython on Ubuntu?

I am writing an application in Python / wxPython. It runs fine on Windows and it runs fine from Eclipse on Ubuntu.

However, if I run it 'directly', either by double-clicking or from a $python filename.py command in terminal then the menubar is not displayed.

Everything else works, including the toolbar

Any ideas?
It is a bug in Ubuntu which uses a different menu system. You need to add this to your launch script:
```
export UBUNTU_MENUPROXY=0
```

---

### Post by pauljwells on 2010-12-17
Thank you stani!!

Would you be the stani of SPE? Big respect!

:)

---

### Post by mindg33k on 2011-07-13
hi 
I've same problem but "export UBUNTU_MENUPROXY=0"
not solved my problem! 
why?

---

### Post by stani on 2011-08-18
> **pauljwells said:**
> Thank you stani!!

Would you be the stani of SPE? Big respect!

:)
Yes, I am.

> **mindg33k said:**
> hi 
I've same problem but "export UBUNTU_MENUPROXY=0"
not solved my problem! 
why?
In Natty wx applications show the menu right out of the box.

---

### Post by _ManuelArango on 2011-11-23
That is the same problem i have. 
Could anyone of you tell me how to solve the problem of the menu out of the box please?

---

### Post by stani on 2011-11-26
> **_ManuelArango said:**
> That is the same problem i have. 
Could anyone of you tell me how to solve the problem of the menu out of the box please?
This issue is a bug in Unity, not wxPython. It is fixed in Ubuntu Oneiric, so upgrade your ubuntu distro and it will be solved out of the box.

---

### Post by tkro on 2012-11-09
Even if the bug has been fixed in oneiric, it seems to be back in precise? Tried stani's fix (if I got it right) and added  "export UBUNTU_MENUPROXY=0" to /etc/rc.local (before the last line exit 0). Rebooted. Now wxpython menus disappear from the app window, and do not appear in the top bar any more. So - it's gone from bad to worse for UNITY. Back in Gnome the menus still appear where I expect.

---

