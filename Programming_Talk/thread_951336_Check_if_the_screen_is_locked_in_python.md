---
title: "Check if the screen is locked in python?"
date: 2008-10-18
forum: Programming Talk
---

### Post by abeisgreat on 2008-10-18
Is there someway in a python script to check if the screen is locked? I googled, but no luck.

Thanks for the help,
Abe

---

### Post by loell on 2008-10-18
you could use **os.system() or os.popen()**

to monitor xscreensaver by executing

```
xscreensaver-command -watch
```

from there, you can catch whenever the screen is locked through its state output named **"lock"**.

---

### Post by abeisgreat on 2008-10-18
> **loell said:**
> you could use **os.system() or os.popen()**

to monitor xscreensaver by executing

```
xscreensaver-command -watch
```

from there, you can catch whenever the screen is locked through its state output named **"lock"**.
Alright thats for the advice I think ive got it worked out

---

