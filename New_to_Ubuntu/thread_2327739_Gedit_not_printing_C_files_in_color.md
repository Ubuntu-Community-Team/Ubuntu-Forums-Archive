---
title: "Gedit not printing C files in color"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by schmitta on 2016-06-13
I know there is a patch for this. I removed and installed gedit but it still prints in black and white. I have 64 bit 14 something (LTS) Ubuntu. (Just installed 64 bit).  I know there is a patch but I don't know how to install it.

---

### Post by ashwin.kj on 2016-06-14
I may be wrong, but Gedit should be automatically doing this without any patch (if it is able to detect that the file is C). Check in the status bar to see if it is detected as C file else choose C from the list. See the attached screenshots
[ATTACH=CONFIG]269575[/ATTACH]
When properly detected it should be some thing like this
[ATTACH=CONFIG]269576[/ATTACH]

---

### Post by mc4man on 2016-06-14
> **schmitta said:**
> I know there is a patch for this. I removed and installed gedit but it still prints in black and white. I have 64 bit 14 something (LTS) Ubuntu. (Just installed 64 bit).  I know there is a patch but I don't know how to install it.

bug report, should be a gtksourceview3 patch attached- 
[https://bugs.launchpad.net/ubuntu/+source/gtksourceview3/+bug/1313283](https://bugs.launchpad.net/ubuntu/+source/gtksourceview3/+bug/1313283)
If you don't want to rebuild yourself try here - 
[https://launchpad.net/~mc3man/+archive/ubuntu/color-print](https://launchpad.net/~mc3man/+archive/ubuntu/color-print)

---

