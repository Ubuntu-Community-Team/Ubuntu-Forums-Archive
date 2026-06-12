---
title: "[SOLVED] Screensaver"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Java Geek on 2008-09-08
umm...I need to set a screensaver in xubuntu but all I end up getting is my monitor turning off. That is not really a problem except that it takes like 30 secs for my monitor to warm up. I need to just make it so that it does my screensaver

---

### Post by cek on 2008-10-16
I was having a problem with screensaver as well -- you will read a lot of bugs with compiz, etc., but none of that fixed my issue.


There were no errors in any logs about screensaver failing to start, so I tried running it from the command line:  (gnome-screensaver) and it worked as expected, even used the options I had set in the Settings Manager.

My thought here is that for some reason gnome-screensaver wasn't launching as it was supposed to be.

I simply added gnome-screensaver to my list of auto started applications (via Settings Manager) and now its working as expected.

---

### Post by Java Geek on 2009-01-02
sorry its taken so long to reply but my system has been suffering from fatal errors that are now fixed (sorta) thanks it works as expected

---

