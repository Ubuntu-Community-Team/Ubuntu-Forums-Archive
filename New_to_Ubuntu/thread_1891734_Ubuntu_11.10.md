---
title: "Ubuntu 11.10"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by ahrar25 on 2011-12-06
i have ati radeon 4850 gfx card,,, why it has no good support for linux?? i mean when i drag window on my desktop its not smooth,,, i am  using ubuntu 11.10... i also had downloaded its driver... and is upto date any clues???

---

### Post by 3rdalbum on 2011-12-06
If your mouse has a high sampling rate, this may be contributing to a bug. I can't remember the name of the bug so I can't send you a link to the bug report, but in effect it causes the windows to only move and redraw about once per second when you're moving them.

This is nothing to do with your graphics card. It's a bug in the window manager that's usually invisible, but only comes out when the mouse samples at a high rate. If your mouse has a sampling rate switch, try turning it down to the lowest.

---

