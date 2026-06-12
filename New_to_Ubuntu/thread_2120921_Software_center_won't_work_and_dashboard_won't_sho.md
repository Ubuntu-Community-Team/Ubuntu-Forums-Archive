---
title: "Software center won't work and dashboard won't show any programs"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by JRay88 on 2013-02-27
Title says it all. The software center turns dark and freezes, the dashboard will show you all the files I've recently viewed but none of the programs.

---

### Post by Krytarik on 2013-02-27
Try clearing Software Center's cache, it should fix both:
```
rm -rf ~/.cache/software-center
```If you wonder why the Unity Dash is affected by that too, please see [here]("http://ubuntuforums.org/showthread.php?p=11636422#post11636422").

Regards.

---

