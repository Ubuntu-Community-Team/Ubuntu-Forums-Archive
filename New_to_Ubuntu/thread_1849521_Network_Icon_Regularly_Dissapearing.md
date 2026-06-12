---
title: "Network Icon Regularly Dissapearing"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by RussianSoup on 2011-09-24
[SIZE=2]Hey all,
I've been having some trouble ever since I first installed Ubuntu, and looking around online I've come across people who have this happen once or twice, but not regularly.

I'm running 11.04 on my Toshiba NB205, it seems almost every time I lose my network connection the network manager disappears from my top panel and I become unable to connect without logging out and back in to restore it. This happens both when I'm using wifi and when I have a mobile broadband connection. Any ideas on possible causes and, more importantly, fixes?[/SIZE] [SIZE=2]

Thanks in advance guys. Let me know if you have any questions on specs and I'll see if I can dig them up.[/SIZE]

---

### Post by Leppie on 2011-09-24
if network manager is still running, you should be able to restore its icon (and other missing icons) in the notification area like this:
```
killall gnome-panel
```

---

### Post by RussianSoup on 2011-09-24
> **Leppie said:**
> if network manager is still running, you should be able to restore its icon (and other missing icons) in the notification area like this:
```
killall gnome-panel
```
Leppie,
Thanks, good easy fix, if not somewhat brutish. Still looking for a cause and prevention ideas though.

---

### Post by Leppie on 2011-09-24
> **RussianSoup said:**
> Leppie,
Thanks, good easy fix, if not somewhat brutish. Still looking for a cause and prevention ideas though.
the gnome-panel app seems to play tricks since lucid...

---

