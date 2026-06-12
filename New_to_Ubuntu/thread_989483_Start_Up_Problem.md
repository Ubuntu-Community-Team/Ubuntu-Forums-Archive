---
title: "Start Up Problem"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by bigal1932flying on 2008-11-21
SOLVED : I tried to fix the 8.10 sound problem and all I managed to do was stuff up Start Up. Ibex now does not start normally and the "~/:xsession-errors file reads:

/etc/gdm/Xsession : Beginning session setup ...
Setting IM through im-switch for local =en_AU
Start IM through /etc/x11/xinit/xinput.d/all_ALL linked to /etc/x11/xinit/xinput. d/default.
user/bin/xmodmap: unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap: 1 error encounted, aborting.
Couldn't exec /usr/bin/pulse-session: Permission denied.

Can someone PLEASE tell me how to fix this problem?
THANKS in advance.

---

### Post by kansasnoob on 2008-11-21
I would run:

```
sudo dpkg-reconfigure -phigh -a
```

That should basically reconfigure everything!

---

### Post by bigal1932flying on 2008-11-25
sudo dpkg-reconfigure -phigh -a does not fix the problem.
Is there something else I can do?

---

### Post by mapes12 on 2008-11-26
Looks like the X server has become corrupted. If you can get to a Terminal try reinstalling your desktop environment with ```
sudo apt-get install ubuntu-desktop
```

---

