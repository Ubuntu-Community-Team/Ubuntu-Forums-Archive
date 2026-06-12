---
title: "Lost my sound all of sudden!!!!"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by appoloin on 2008-06-07
for some strange reason i have no sound at all and im getting this error;
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

how can i fix this?

---

### Post by Nepherte on 2008-06-07
Did sound work on your system before?

Could you post the output of:
```
lspci
``` and ```
aplay -l
```

---

