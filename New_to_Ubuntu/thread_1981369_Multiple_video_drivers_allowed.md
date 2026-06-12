---
title: "Multiple video drivers allowed?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-16
I am still having problems installing the correct NvDia driver.

I wonder if multiple video drivers will be allowed and that upon boot the correct driver would be automatically selected?

---

### Post by Boyntonstu on 2012-05-17
Bump

---

### Post by idoitprone on 2012-05-17
> **Boyntonstu said:**
> Bump

ummmm it not a good idea to have multiple drivers installed because it cause a race condition.

We debug all of wireless problems because multiple video drivers are installed

to check you drivers 
```
lspci -nnk
```

---

### Post by Boyntonstu on 2012-05-17
> **idoitprone said:**
> ummmm it not a good idea to have multiple drivers installed because it cause a race condition.

We debug all of wireless problems because multiple video drivers are installed

to check you drivers 
```
lspci -nnk
```

Thanks!

---

### Post by idoitprone on 2012-05-17
> **Boyntonstu said:**
> Thanks!

my stupidity

We debug alot of wireless prblems because they install different drivers for the same card

---

