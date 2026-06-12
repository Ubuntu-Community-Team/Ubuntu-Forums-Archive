---
title: "Light DM-Invalid UTF-8"
date: 2011-08-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rifester on 2011-08-14
Is anybody else seeing this at the top right corner of the login screen?  I see it at every login and can't seem to find a bug about it...

---

### Post by cariboo on 2011-08-14
If you run lightdm in test mode does the error message show?

If you haven't got xserver-xephyr installed, install it first, then open a terminal and type:

```
lightdm --test-mode
```

A screenshot would be nice.

---

### Post by Rifester on 2011-08-14
I followed your instructions and the error  does not show up in test mode.    I rebooted but still have the UTF error right beside the name in the upper right corner.   Not sure how to get a screen shot of the login screen.

---

### Post by Rifester on 2011-08-14
Screenshot:

---

### Post by Gunss on 2011-08-14
The same issue here!

fully updated system.

---

### Post by MacUntu on 2011-08-14
[https://bugs.launchpad.net/indicator-session/+bug/811852](https://bugs.launchpad.net/indicator-session/+bug/811852)

---

### Post by Rifester on 2011-08-14
Thanks!

---

