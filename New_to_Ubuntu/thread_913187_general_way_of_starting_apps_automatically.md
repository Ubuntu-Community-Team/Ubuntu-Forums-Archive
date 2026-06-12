---
title: "general way of starting apps automatically"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by dgrafix on 2008-09-07
Is there some kind of common .rc file that can run several commands automatically when a user logs in?

This a general linux question, but is specific to XFCE .

---

### Post by M4rotku on 2008-09-07
Yes,  /etc/rc.local

Just add the lines you want before the exit command.

Good luck

---

### Post by txcrackers on 2008-09-07
Actually, *rc.local* is only used when the computer starts up.

For a user logging in, there are several options:

_Console/Terminal_
*$HOME/.bashrc* - commands in this file get executed on each login - which includes opening terminal screens. Unique to each user.
*/etc/profile.d* - any executable script in this directory gets executed for each user when they login. Global for all users.

_X_
The X startup goes through an even *more* complicated set of scripts and you have a lot of options. I'm not even going to enumerate them all, but here's some reading material (appropriate man pages): X, xinit, startx

No matter what you do, if you're messing with "global" configurations, make backups or at least know how to get out of any holes you dig for yourself as you're experimenting...

---

