---
title: "[SOLVED] file permissions in /opt"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Jacroe on 2008-11-28
I got it. Nevermind

---

### Post by Bölvaður on 2008-11-28
Alt+F2
Write

```
gksudo nautilus /opt/
```

That will run nautilus as root user, so be careful.
I guess you know you change users and permissions from properties (right click gets you to it)

terminal commands for something similar to what you might be doing:
```
cd /opt/
sudo chown user lampp/
sudo chmod g+w lampp/
```

---

