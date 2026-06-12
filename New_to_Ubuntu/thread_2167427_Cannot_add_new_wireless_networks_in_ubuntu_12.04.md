---
title: "Cannot add new wireless networks in ubuntu 12.04"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by pirritx on 2013-08-13
I changed the system from ubuntu 10.04 to ubuntu 12.04. Now, I can't add new wireless networks. When i press the add button, the eindow appears, but the 'save' and 'available to all users' buttons are disabled (grey). Why does this happen?

---

### Post by newbie-user on 2013-08-13
Try this. In the file /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy go to line 695. Edit the line to look like this:
```
<allow_active>auth_admin_keep</allow_active>
```

Then restart.

---

