---
title: "Is gksu nautilus the way to go for changing files..."
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Toronto11 on 2012-02-22
if you don't know the terminal command?

I want to enter this line in the alsa-base.conf file:

options snd-hda-realtek model=auto =enable=1 index=0

---

### Post by alphacrucis2 on 2012-02-22
> **Toronto11 said:**
> if you don't know the terminal command?

I want to enter this line in the alsa-base.conf file:

options snd-hda-realtek model=auto =enable=1 index=0


No. 

```
gksu gedit
```

Or use nano.

Best not run nautilus as admin unless you really really need to.

---

