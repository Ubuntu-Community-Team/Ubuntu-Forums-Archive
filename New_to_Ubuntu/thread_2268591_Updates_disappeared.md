---
title: "Updates disappeared"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by h_piper on 2015-03-10
When I logged into Ubuntu today I saw that there were some system software updates waiting to be installed but I had a couple other things to do. When I was done I went to install the updates and they are gone. The update icon over on the left edge of the screen is gone. I waited a while thinking it would pop back up but it never did. Is there someway to manually get the system to update? Will that update Icon show back up eventually?

---

### Post by Bucky Ball on 2015-03-10
Go to Software Updater and update (might be called something different in Ubuntu, but similar - search in Dash).

You can update anytime via a terminal with:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

