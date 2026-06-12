---
title: "Desktop Framerate"
date: 2018-12-05
forum: New to Ubuntu
---

### Post by joephnarro on 2018-12-05
Running on a 144hz monitor, I can see that some elements of ubuntu do successfully run at 144 fps, including most of the applications themselves, and the cursor. However some things, for example this menu opening animation that runs at max 60 fps probably less, don't run smoothly.

[ATTACH=CONFIG]281886[/ATTACH]

Is there a way to get these things running at 144 fps, or is this inconsistency just something to get used to?

---

### Post by CatKiller on 2018-12-05
I haven't used a default Ubuntu window manager in quite a while, but compositing window managers generally try to find out the refresh rate to use with their display, and have a place where you can enter the refresh rate if they get it wrong. You'll probably find it in the settings somewhere.

Edit: looking at Gnome's changelogs it seems that this wasn't fixed till four months ago for them. So maybe it's made it in, maybe it hasn't.

---

