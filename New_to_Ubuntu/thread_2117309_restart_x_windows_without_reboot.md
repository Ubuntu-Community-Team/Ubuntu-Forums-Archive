---
title: "restart x windows without reboot"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by marchelloUA on 2013-02-18
Hi all, 

how do I restart x windows without PC reboot ?

---

### Post by PowerBarry43 on 2013-02-18
Hi

Try 

```
sudo restart lightdm
```

also depending on your desktop it could be:

```
sudo restart gdm

sudo restart kdm
```

these will work from ubuntu 11.10 or later, prior tot that you run

```
sudo service lightdm restart
```

hope this helps!

Barry

---

### Post by HermanAB on 2013-02-18
X is restarted when you log in.  So, just log out and log in again.

---

