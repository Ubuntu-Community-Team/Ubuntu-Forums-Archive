---
title: "Just removed WICD, can't get Gnome-Network working"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by neurostu on 2008-05-06
So I ran:
```

sudo apt-get remove wicd
sudo apt-get install network-manager network-manager-gnome

```
I can connect to the internet now (over LAN), I just don't have the little applet that lets me select which wireless network to connect anymore, does anybody know how to restore it?

And it isn't the "Network Monitor" I added that to my panel but it  what I was looking for.

---

### Post by twright on 2008-05-06
try typing nm-applet into terminal

---

### Post by neurostu on 2008-05-06
Thats it! Thanks!

---

