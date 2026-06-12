---
title: "control remotely."
date: 2014-03-09
forum: New to Ubuntu
---

### Post by kevin67 on 2014-03-09
I am completely new to ubuntu. I have never messed with it but have been wondering for some time now. I host source game servers and have a server box rented out of chicago. I just installed ubuntu 13.10 on to it and have to do everything remotely. Can someone help me out on being able to view desktop remotely?

---

### Post by CharlesA on 2014-03-09
If you are renting a VPS, it shouldn't have a GUI installed by default. Use SSH.

---

### Post by kevin67 on 2014-03-09
alright so is there a way for me to install a gui?

---

### Post by CharlesA on 2014-03-09
You could, but if you are going to be running source servers, you will probably want all the resources you can get.

```
apt-get install ubuntu-desktop --no-install-recommends
```

It would be better to just run your servers in screen sessions, but to each their own.

---

