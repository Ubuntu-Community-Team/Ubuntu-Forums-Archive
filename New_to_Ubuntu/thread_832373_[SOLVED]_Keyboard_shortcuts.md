---
title: "[SOLVED] Keyboard shortcuts"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-17
I tried to create shortcuts for some apps. But some work and some don't.

I went to Settings>>Keyboard Settings. I had to create a new Theme on the shortcut tab since it wouldn't let me modify shortcuts otherwise. 
I added the following four shortcuts
```
xfce4-terminal       Super + t
/usr/bin/firefox      Super + w
/usr/bin/rtorrent    Super + r
/usr/bin/cplay       Super + c
```The first two for the terminal & firefox work fine, but the ones for rtorrent and cplay do not !

:confused:

Is this because these are terminal apps? How do I invoke them in a terminal?

How do I make the shortcuts for those apps?

---

### Post by Inxsible on 2008-06-17
Ok I got it.

We have to use the terminal to pull those apps up. I used the following commands for the shortcuts```
 xfce4-terminal -T "cplay" --working-directory="/media/WD500/Music" -x /usr/bin/cplay
```I then set the shortcut to Super + c

The command for rtorrent was```
xfce4-terminal -T "rTorrent" -x /usr/bin/rtorrent
``` Shortcut was Super + t. This command does not have a working directory because it always uses the rtorrent.rc to get its settings from.



I thank myself ;-)

---

