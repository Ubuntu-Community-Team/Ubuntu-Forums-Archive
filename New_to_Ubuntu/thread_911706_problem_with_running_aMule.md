---
title: "problem with running aMule"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by emrahustun on 2008-09-05
Hello friends.
amule was working good but suddenly whatever happened, it's not working now.
Double click does nothing, and from terminal i'm taking "Amule is already running" error. But it's not running. I can't see in system monitor anyway.

I've uninstalled and installed again it didn't changed.

Can you help?

Thank you all...

---

### Post by wolfen69 on 2008-09-05
to check to see if it's running, go to system>administration>system monitor>processes and kill it from there. also, removing and reinstalling wont work unless you do *sudo apt-get clean* and *sudo apt-get autoremove* before reinstalling.

---

### Post by emrahustun on 2008-09-06
Thank you. But i can't see in the system monitor. Anyway, i'm looking right after reboot.
Now i'm gonna try removing as you told.

---

### Post by emrahustun on 2008-09-06
Thank you wolfen69.
After
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get autoclean
```
it's working now.

---

