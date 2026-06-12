---
title: "[SOLVED] CL Debian List all packages"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-18
Is there a way to list all packages you have installed via the command line?

---

### Post by brian_p on 2008-06-18
> **AnLGP said:**
> Is there a way to list all packages you have installed via the command line?

Full detail:

```
dpkg -l
```

Names only:

```
dpkg -l | awk '{print $2}'
```

---

