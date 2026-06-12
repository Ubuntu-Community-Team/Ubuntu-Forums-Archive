---
title: "reloading kernel modules..?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by adza on 2008-08-18
Hi There, i've just been tinkering with trying to get my WM device syncing with ubuntu and have unloaded some kernel modules... turns out i shouldn't have (doh!)... how can i reload these modules?

---

### Post by amo-ej1 on 2008-08-18
```

modprobe module_name

```

(you could use rmmod module_name to remove a module)

---

