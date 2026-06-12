---
title: "Dual monitor problems"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Hex9 on 2013-03-16
Hi,

Im having trouble with my dual monitors, i have dualled before with no issues but i was using another computer/monitor.

When i take it off mirror mode is system settings it spits out:

The selected configuration for displays could not be applied.
required virtual size does not fit available size: requested=(3200, 900), minimum=(320, 200), maximum=(1920, 1920)

Monitors res: 1600x900
                   1920x1080

Im pretty sure its a driver problem, as i have installed my amd driver not too long ago.
Has anyone ran into the same issue?

Thanks

---

### Post by QIII on 2013-03-16
What model is the video adapter?

When you installed the driver, did you do

```
sudo amdconfig --initial
```

---

### Post by Hex9 on 2013-03-16
The graphics card is a 6970, i dont remember running the command, i just did but nothing changed.

---

