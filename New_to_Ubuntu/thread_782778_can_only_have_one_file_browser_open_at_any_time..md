---
title: "can only have one file browser open at any time."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-05-05
if i open a second/third/etc file browser than it shows a black blank under the window border. i think that it is to do with compiz-fusion, i think i will try to run konqueror as a side file browser for now till i can fix it. any help appreciated.

edit- turns out both add/remove and synaptic package manager show black screen as well, maybe reboot will fix. will try that when other processes finish.

---

### Post by northern lights on 2008-05-05
If you wanna check whether your issue is compiz related, simply run ```
metacity --replace
``` and see whether things are working. You can install konqueror via ```
sudo apt-get install konqueror
```

---

