---
title: "[SOLVED] Screen brightness problems"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by scotcella on 2008-05-23
Hi, been trying to find information via a search but couldn't find anything relevant.

How do I adjust the screen brightness in Linux?

My laptop dual boots with Vista as well, so I know the buttons are in working order. If it helps I have a Sony Vaio, so the screen brightness adjusty thingy uses the Fn key plus F5 (darker) and F6 (brighter).

FOr some reason it doesn't work in Ubuntu. Can anyone help me with this? I tried looking in the Powersettings, and Screensaver but didn't find anything.

Many thanks in advance!

Edited to add that I'm obviously using the latest Version, Hardy.

---

### Post by KingTermite on 2008-05-23
scotcella,

Try this command from a terminal window.

> sudo gconf-editor

Somebody in another post recently showed that. There are tons of finer tweaks like that in the Gnome configuration. I think brightness may be in there.

---

### Post by scotcella on 2008-05-23
I solved this issue-

I right clicked on the panel and found an applet that adjusts screen brightness.

Yay

Thanks KingTermite

---

