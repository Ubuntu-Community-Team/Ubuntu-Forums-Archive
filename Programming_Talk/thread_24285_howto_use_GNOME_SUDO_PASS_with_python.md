---
title: "howto use GNOME_SUDO_PASS with python?"
date: 2005-04-06
forum: Programming Talk
---

### Post by wfx on 2005-04-06
hi,
some code like this does not work:
```
#!/usr/bin/python
import os
os.popen("/usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/sbin/ANYAPP")
```

---

