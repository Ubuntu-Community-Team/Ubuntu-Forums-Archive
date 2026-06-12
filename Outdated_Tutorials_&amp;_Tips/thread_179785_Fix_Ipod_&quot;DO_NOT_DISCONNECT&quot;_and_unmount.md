---
title: "Fix Ipod &quot;DO NOT DISCONNECT&quot; and unmount errors"
date: 2006-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by %hMa@?b&lt;C on 2006-05-20
simply one command will fix this.  It allows the ipod to actuall be disconnected fully before unpluggin open up terminal and type
```
sudo chmod +s `which eject`

```

---

### Post by %hMa@?b&lt;C on 2006-05-23
Update: Ipod Must Not Be On "hold"

---

### Post by aysiu on 2006-05-23
So is that a one-time fix, or does that command need to be run every time you want to disconnect the iPod?

---

### Post by %hMa@?b&lt;C on 2006-05-24
[QUOTE=aysiu]So is that a one-time fix, or does that command need to be run every time you want to disconnect the iPod?[/QUOTE]
this is a one time fix, run it once, works forever

---

### Post by aysiu on 2006-05-24
[QUOTE=jeffc313]this is a one time fix, run it once, works forever[/QUOTE] Awesome. It's better than running ```
sudo eject /media/ipod
``` every time!

---

