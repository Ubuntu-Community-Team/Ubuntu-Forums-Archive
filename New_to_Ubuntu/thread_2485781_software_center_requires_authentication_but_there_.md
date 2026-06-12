---
title: "software center requires authentication but there is no way to provide it"
date: 2023-04-09
forum: New to Ubuntu
---

### Post by kennthhz on 2023-04-09
I am running 22.04.2 LTS. When I open the software-center GUI to upgrade apps or install new app, it pops up error "authentication required" but the GUI doesn't provide anyway to provide authentication. When I try to "sudo snap-store" it failed as well.

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy

---

### Post by MAFoElffen on 2023-04-10
Have you tried
```

sudo apt install --reinstall gnome-software

```
to see if reinstalling it resolves that problem?

---

