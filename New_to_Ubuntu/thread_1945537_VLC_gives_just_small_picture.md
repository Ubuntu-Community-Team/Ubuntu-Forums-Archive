---
title: "VLC gives just small picture"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-03-23
I installed VLC, but when I play a movie with it, it only gives me a very small picture in the middle, and I seem to be unable to fix it.  

What can I do about that?

---

### Post by ccrs8 on 2012-03-23
In the "Video" menu, try fiddling with the Zoom or Scale options.

---

### Post by EzioAuditore on 2012-03-23
See if resetting vlc helps. Close vlc if already running then in a terminal enter:
```
rm -f ~/.config/vlc/vlcrc
```
hope it helps.

---

### Post by Carnivorum on 2012-03-23
> **ccrs8 said:**
> In the "Video" menu, try fiddling with the Zoom or Scale options.

Tried those, he doesn't react at all to those.

---

### Post by Carnivorum on 2012-03-23
> **EzioAuditore said:**
> See if resetting vlc helps. Close vlc if already running then in a terminal enter:
```
rm -f ~/.config/vlc/vlcrc
```
hope it helps.

No change

---

### Post by Carnivorum on 2012-03-24
After giving my comp a break, and restarting it, VLC behaves now very well and the problem is gone. 

What I want to know now, is how to minimize the VLC player to the tray, without closing it. 

Now, if I want to pause it, and do something else on my comp, I have no choice than to close it completely, because  I don't see a button to minimize it. 

What can I do about that?

---

### Post by Carnivorum on 2012-03-24
I figured it out, I have to unmark the "full screen" option.  

Thanks everybody.

---

