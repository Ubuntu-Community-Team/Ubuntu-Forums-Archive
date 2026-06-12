---
title: "Pidgin Notifications"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by ickyplush on 2008-10-15
Just a quick check to see if anyone has heard anything about a (dare i say it) MSN like system for notifying you when someone signs into pidgin?
Much thanks

---

### Post by Sarmacid on 2008-10-15
Go into synaptic and install pidgin libnotify. Then go to pidgin and it should be under plugins for you to configure.

---

### Post by ickyplush on 2008-10-15
what source is it under?
I'm getting nothing in termina (Synaptic is being a little stubborn and not starting)
got an apt-get for it?

---

### Post by howefield on 2008-10-15
try updating sources

```
sudo apt-get update
```

I have it in mine, the only extra repository I have is Medibuntu.

---

### Post by Sarmacid on 2008-10-15
Try

```
sudo apt-get install pidgin-libnotify
```

---

### Post by ickyplush on 2008-10-15
Cheers that'll be the ticket!

---

