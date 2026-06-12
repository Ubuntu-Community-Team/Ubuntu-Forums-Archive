---
title: "how to uninstall python 3.2.3"
date: 2012-04-16
forum: Programming Talk
---

### Post by vexaxv on 2012-04-16
i installed the new python by source and i didnt do checkinstall..theres no uninstall file..how do i uninstall it?

---

### Post by Hetepeperfan on 2012-04-17
> **vexaxv said:**
> i installed the new python by source and i didnt do checkinstall..theres no uninstall file..how do i uninstall it?

sometimes 

```
sudo make uninstall 
```does the trick

if you want to rebuild it you should also run:
```
make clean 
```
this one shouldn't require sudo powers.

Kind regards.

---

