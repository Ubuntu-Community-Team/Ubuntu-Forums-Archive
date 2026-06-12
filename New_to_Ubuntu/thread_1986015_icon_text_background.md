---
title: "icon text background"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by Rien X on 2012-05-24
Hi. I just moved from Win7 to Xubuntu12 and so far I'm very pleased and impressed. I don't care much for eye candy but one thing really bugs me in the Xubuntu desktop and I can't figure out how to get rid of it: the white background behind the icon texts on the desktop. Anybody? Please?

---

### Post by Rodney9 on 2012-05-24
TIP from - [http://tinyurl.com/6tagjjj](http://tinyurl.com/6tagjjj)

If you have some icons on your desktop, you may have wished to remove those borders around their text labels (see image below). If so, it can be done relatively easily:

- use your terminal to type:
leafpad ~/.gtkrc-2.0

- paste this in a newly opened Leafpad window:
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0
fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#000000" }
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

- save and close Leafpad & Log out/Log in.

---

### Post by Rien X on 2012-05-24
That's just what I needed. Thanks!

---

### Post by vasa1 on 2012-05-24
Then you could mark the thread as "solved" by using the thread tools near the top of the page on the right.

---

