---
title: "Where's my root terminal??"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Cybergrinder on 2008-05-16
Hi all,

I recently upgraded from Hoary to Gutsy Gibon (7.10) and now when I try to install the sound codecs I get an error that I dont have rights. I logged in as full access to all systems but still can't create a folder. 

I remember on Hoary that there was a terminal window which opened as the current user, and then a root terminal which allowed complete access. PLease help!

---

### Post by fontenot_1031 on 2008-05-16
```
sudo su
``` works well in this case.

---

### Post by aysiu on 2008-05-16
Open a regular terminal and type ```
sudo -i
```

---

