---
title: "How do I COMPLETELY remove deluge?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by 449 on 2008-05-16
When I try to completely remove deluge it doesn't. Is there any way to start afresh with this program?

---

### Post by Joeb454 on 2008-05-16
Try running this from a terminal ```
sudo aptitude purge deluge
``` and see if that works :)

---

### Post by zvacet on 2008-05-17
```
sudo dpkg --remove --force-remove-reinstreq deluge
```

---

