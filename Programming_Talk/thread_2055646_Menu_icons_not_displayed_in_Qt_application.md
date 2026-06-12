---
title: "Menu icons not displayed in Qt application"
date: 2012-09-09
forum: Programming Talk
---

### Post by gibbogle on 2012-09-09
I have ported a Qt program from Windows to Ubuntu 12.04, building it with Qt Creator (4.6 on Windows, 4.8 on Ubuntu).  The menu icons are visible in Qt Designer, but they are not displayed at run time.  (All is good in Windows.)

I found suggestions about using gconftool to tell gnome that I want to see icons, e.g.:
gconftool-2 --type boolean --set /desktop/gnome/interface/buttons_have_icons true
but this makes no difference.  I wonder if anyone else has encountered this problem.

Thanks
Gib

---

### Post by SledgeHammer_999 on 2012-09-09
Look at answer #11 ->[https://bbs.archlinux.org/viewtopic.php?pid=940213#p940213](https://bbs.archlinux.org/viewtopic.php?pid=940213#p940213)

For buttons and menus:
```
gconftool-2 --type boolean --set /desktop/gnome/interface/buttons_have_icons true
gconftool-2 --type boolean --set /desktop/gnome/interface/menus_have_icons true
```

---

