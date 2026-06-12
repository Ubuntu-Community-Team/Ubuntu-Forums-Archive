---
title: "HOW-TO disable the ANOYING PC SPEAKER beeping for now and for ever"
date: 2008-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by mendozaro on 2008-11-05
**1. Stop it NOW (it will beep again after a restart):**

```
sudo modprobe -r pcspkr
```

**2. Stop the beeping FOR EVER! (will work after a restart)**

2.1 Fire up a terminal and type:
```
sudo gedit /etc/modprobe.d/blacklist
```

2.2 Add to the end of the opened file the following line:
```
blacklist pcspkr 
```

2.3 Save and close the opened file

---

