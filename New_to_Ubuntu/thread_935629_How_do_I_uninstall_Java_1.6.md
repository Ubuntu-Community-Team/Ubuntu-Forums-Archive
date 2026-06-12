---
title: "How do I uninstall Java 1.6?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Warpster Buntu on 2008-10-01
I think some of the sites and apps I use I go onto are not up to date with their Java programming.

So I'd like to install 1.5

---

### Post by GhentK on 2008-10-01
Did you install it through APT (add/remove or Synaptics) or with a self-executable from java.com?

---

### Post by Warpster Buntu on 2008-10-01
From Java.com

---

### Post by Crafty Kisses on 2008-10-01
You can uninstall it the same way you installed it. Just add --uninstall at the end.

---

### Post by Warpster Buntu on 2008-10-01
What would be the terminal command?

---

### Post by GhentK on 2008-10-02
It would seem that the installer in fact doesn't install anything outside the ./jre1.6* directory you ask it to install in. If you just navigate to the place you installed it (e.g. /usr/java/), you can:

```
sudo rm -R ./jre1.6.0_07/
```

and it should be gone. :)

---

