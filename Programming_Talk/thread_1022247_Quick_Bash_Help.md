---
title: "Quick Bash Help"
date: 2008-12-26
forum: Programming Talk
---

### Post by onlyproductions on 2008-12-26
is there anyway to make a part of my code execute at a particular time of day?

---

### Post by ibutho on 2008-12-26
If you mean that you need to tun a particular script or program at a certain time, take a look at cron and at.

---

### Post by onlyproductions on 2008-12-26
> **ibutho said:**
> If you mean that you need to tun a particular script or program at a certain time, take a look at cron and at.

i need to make a script that i can open and run in the background and will open at 2pm everyday

---

### Post by matmatmat on 2008-12-27
Try using something like this:
```

at 2.00
at>do something

```
use that if you only want to use it once or use
```

crontab -e

```

---

