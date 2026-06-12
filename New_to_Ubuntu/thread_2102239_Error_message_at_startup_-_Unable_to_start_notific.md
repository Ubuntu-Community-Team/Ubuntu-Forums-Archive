---
title: "Error message at startup - Unable to start notification daemon"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by NonStop on 2013-01-06
[http://img842.imageshack.us/img842/3134/201301062207441440x900s.png](http://img842.imageshack.us/img842/3134/201301062207441440x900s.png)

Hey people, above is the current error I get when turning on my machine, been getting it since i upgraded to 12.10. Any ideas on how to stop it? Generally I jsut exit it and all is fine.

---

### Post by mysteriousdarren on 2013-01-07
I would just uninstall xfce4 notifications unless you would just want to uninstall the other notifications that are installed. I use gnome and xfce and ran into this a while back.

---

### Post by NonStop on 2013-01-07
Thank you for the reply, how would I go about doing that?

---

### Post by mysteriousdarren on 2013-01-11
Go into synaptic package manager, and search xfce. Completely remove it. If you continue to have trouble just post a screenshot of what your screen has for notifications or list them.

---

### Post by mmortal03 on 2013-04-29
> **mysteriousdarren said:**
> Go into synaptic package manager, and search xfce. Completely remove it. If you continue to have trouble just post a screenshot of what your screen has for notifications or list them.
This didn't work for me, because it said that lubuntu desktop would also be removed. Instead, I removed notification-daemon, and this solved the problem.

---

