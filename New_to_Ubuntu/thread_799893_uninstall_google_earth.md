---
title: "uninstall google earth"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-19
I installed google earth but it  not working properly.  How can I uninstall it?

Thanks

---

### Post by overdrank on 2008-05-19
> **saskatchewan said:**
> I installed google earth but it  not working properly.  How can I uninstall it?

Thanks

HI and how did you install it? Have you tried synaptic manager to remove it? You can try the command ```
sudo apt-get remove --purge "package name"
``` use the correct package name in place without the quotes.

---

### Post by stchman on 2008-05-19
> **saskatchewan said:**
> I installed google earth but it  not working properly.  How can I uninstall it?

Thanks

If you installed via synaptic then use:

```
sudo apt-get autoremove googleearth
```

Then remove residual config in Synaptic.

If you installed via the .bin file from GE website it is a bit more tricky.

Remove the /opt/googleearth folder
Remove the googleearth in /usr/bin
Remove the menu entry.

---

