---
title: "[SOLVED] Return Panels to default configuration"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-11-25
Hi!

Is there a way (besides putting everything back manually) to return the panels to their default configuration?

Thanks in advance!

---

### Post by amauk on 2008-11-25
delete ~/.gconf/apps/panel directory
```
rm -r ~/.gconf/apps/panel
```

log out and log back in again
panels will be reset to default

---

### Post by bhadotia on 2008-11-25
Delete the ~/.gconf file. This will also delete other settings but they can be configured again easily.

EDIT:
Follow amauk, that's much better a solution :)

---

### Post by pi.boy.travis on 2008-11-25
Excellent!  A certain *someone* messed with their account's panel settings, and needed them returned to default.

Thanks!

---

