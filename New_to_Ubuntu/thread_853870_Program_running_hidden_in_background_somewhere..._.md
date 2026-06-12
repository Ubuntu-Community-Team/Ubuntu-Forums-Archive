---
title: "Program running hidden in background somewhere... not on taskbar"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by brnetonboy on 2008-07-09
I told firefox to automatically open a torrent file with Transmission Bittorrent Client. It worked once. (But then I closed the program.) But the next time I did it it didn't fire up the program (seemingly). I am double clicking all over the torrents to open them but nothing happens.

Finally I find Transmission BitTorrent Client in the menu and try to open it there, but it says : "Another copy of Transmission is already running"

So where is it? Running in the background somewhere? I've tried alt + tab app switching, it's not there. It's not hiding behind any windows... Is there some way to see all running programs? In windows, you can easily press ctrl alt del and see all running programs. How do you do this in Linux? Thanks.

---

### Post by kostkon on 2008-07-09
Just go to *System -> Administration -> System Monitor* to see all of your running processes.

---

### Post by RiceMonster on 2008-07-09
If you want to close it, you can try running this in a terminal:
```
killall transmission
```

Or, you can kill it from the gnome system monitor. I think it's System > administration > system monitor (sorry, I don't use gnome). There you can access a list of everything running, and you can kill it from there and start it again.

Edit: Oops, too slow.

---

### Post by brnetonboy on 2008-07-09
Thanks! That's what I needed :)

---

### Post by mikethehard on 2008-11-24
ok...i have exactly the same thing going on as above but i dont want to close it.

i can clearly see transmission running in my system monitor, and there's plenty of network traffic. however, i dont want to kill the program, i just want to see it again...how can i restore/maxamise the ap?

cheers




(ps i have added transmission to my startup in sessions - just on the off chance this is relevant to this issue)

---

### Post by mikethehard on 2008-11-24
i noticed, when i closed (X) the program earlier on, it used the minimised graphic, but to the top left of my desktop. again, just incase this is useful.

---

### Post by sriwebads on 2011-08-18
You have asked where it is (Transmission BitTorrent Client), its because of the launcher and its because of Workspace Switcher it will move anywhere its very hard to find sometime.

For your solutions to find it, first click it on the launcher and press ALT + SPACE BAR from that from that click MOVE menu, and now move your mouse.

> **brnetonboy said:**
> Thanks! That's what I needed :)

---

### Post by Elfy on 2011-08-18
close 3 year old thread.

---

