---
title: "Delete 'facebook' in message menu"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-05-12
Hi, I have a small problem. First time I visited Facebook on my Chromium, it asked me, if I wan't to install a facebook app. The facebook app is useless, it is just link from my menu and message menu to facebook. However I don't know, how to uninstall It (from the messages menu). I tried: ```
sudo apt-get autoremove facebook
``` but it did not find the package.

Thank you for any help.

[ATTACH=CONFIG]242519[/ATTACH]

---

### Post by stmiller on 2013-05-12
Try this? 
```

sudo apt-get remove account-plugin-facebook

```

---

### Post by ViliX64 on 2013-05-12
Well, I tried messing up things with a firefox. Then I reinstalled the whole Ubuntu (do not worry, I had it installed only for 4 hours) and then (because of it) appeared a problem with Empathy messenger. So I messed up with firefox and facebook again and it is working now.

---

