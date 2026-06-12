---
title: "Authorizations"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by noorez on 2008-09-05
I have some questions about the Authorizations tool in System-Admin menu.

I wanted to block other uses (except for me) to shutdown the system when other users are logged in when other users are logged in. I went ahead and set a block on the user but it didn't work. When I did a switch user and went in to the other user and tried to shutdown the system, I could. Did I miss something in my configuration?

---

### Post by tuxulin on 2008-09-05
see here
[http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

Tuxulin

---

### Post by nisaky on 2008-09-05
Do you have full authorization? It happens even if _you_ installed ubuntu you don't have all "power" without password. Try pressing ALT+F2 and write:
```
gksudo polkit-gnome-authorization
```
and then configure everything what you want.

---

### Post by noorez on 2008-09-05
hmm....using gksuo didn't make the difference. The only difference I saw were, instead of a permission being granted by me, it is now granted by root....

---

