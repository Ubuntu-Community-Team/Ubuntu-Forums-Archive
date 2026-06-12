---
title: "How to become a SuperUser"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-26
I need to know how to become a superuser to run a line of code my console is telling me to run.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



How exactly do I become a super user tho -.- Cant find anything about it in the "Authorizations" panel.

Thanks

---

### Post by EvilDaemon on 2008-09-26
go into a terminal and type

```
sudo dpkg --configure -a
```

Then enter your password.

---

### Post by Vendettaseve on 2008-09-26
THanks

Wierd how it doesnt ask for your password, just says "Must be superuser blah blah" :D

OH well it worked anyways, thanks for the help

---

### Post by Tatty on 2008-09-26
I recommend you read this page: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

