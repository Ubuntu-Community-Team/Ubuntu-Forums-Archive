---
title: "No ethernet in 8.04"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-26
I can do wireless, so this isn't the end of the world, but I could not get any kind of signal through my ethernet port, which is a DP83815 (MacPhyter) Ethernet Controller.

Any suggestions?

---

### Post by XVII on 2008-06-26
Have you checked your cable?

---

### Post by iaculallad on 2008-06-26
Or try running the command below if it can detect your LAN card:

```
lshw -C network
```

---

