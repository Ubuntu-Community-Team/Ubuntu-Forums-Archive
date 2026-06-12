---
title: "Broken Gnome Games"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by GJ92 on 2008-06-12
I just used the Automatic Update tool, and it updated a couple of the pre-installed games. I try to run one of the games and it loads up the window but nothing else.

(I see the title bar and the outline of the window, but nothing on the window)

---

### Post by wolfen69 on 2008-06-12
go to synaptic and search for gnome-games. completely remove it. then:
```
sudo apt-get clean
```then go back to synaptic and re-install gnome-games.

---

### Post by GJ92 on 2008-06-12
Ah ok thanks - Its simple enough to do, but is there a reason why it "just broke" from an update thats supposed to fix things?

---

### Post by Grishka on 2008-06-12
if it persists, you may want to file a bug report at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu).

---

