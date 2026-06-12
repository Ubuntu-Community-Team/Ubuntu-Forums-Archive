---
title: "[SOLVED] Uninstalling Google Earth completely"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by a.v.l on 2008-06-22
My installation from the Google website using a .bin download worked once only. The next time I tried, the globe wasn't present so I uninstalled it from instructions found in a website.  Now when I go into Application -Internet - Google Earth is till entered there but when I click on it to open it I get this error message.

[B]Could not launch menu item.
Failed to execute child process "/opt/google-earth//googleearth"  (No such file or directory)
[/B]
How do I remove the Google Earth entry from Applications please?

---

### Post by Biggy on 2008-06-22
/opt/google-earth/uninstall

---

### Post by spiderbatdad on 2008-06-22
System>>Preferences>>Main Menu. Click the internet option on the left side then uncheck Google Earth on the right side.

---

### Post by iaculallad on 2008-06-22
Try to uninstall it manually:

```
cd /usr/local/google-earth
sudo sh uninstall
```

---

### Post by a.v.l on 2008-06-23
> **spiderbatdad said:**
> System>>Preferences>>Main Menu. Click the internet option on the left side then uncheck Google Earth on the right side.

Thank you this worked a treat.

---

