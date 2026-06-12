---
title: "where doea gwget store its configuration files?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by legolas_w on 2008-04-29
Hi
Thank you for reading my post
I create a backup of my ~ directory begire installing a new version (8.04) now I want to restore gwget to its state before the new os installation and I can not find any .gwget folder in my backup files? can some one please let me know where does it store its configuration files?

Thanks.

---

### Post by Monicker on 2008-04-29
I'm not positveo in this, but my first thought would be that it uses the global file /etc/wgetrc.  Check to see if you have /home/username/.wgetrc, for options specific to your user account.

You could also try the following command from a terminal:

```
find /backupfiles -iname "*wget*"
```

---

