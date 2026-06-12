---
title: "[ubuntu] Nothing in host file"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by XG4GRhE on 2013-08-05
Hi I am trying to change my host name using sudo gedit /etc/host

then after I entered my password, there is nothing in the pad that comes up

before when i first installed ubuntu, there was a bucnh of text like localhost or some stuff like that, now, all that is gone, i have no idea what i did.

---

### Post by steeldriver on 2013-08-05
Hello and welcome to the forum

Are you sure you're not just mistyping the filename? it should be /etc/host**s** , if you type a filename that doesn't already exist then gedit will open a blank file

Also you should use gksudo not plain sudo for GUI applications

```
**gk**sudo gedit /etc/host**s**
```

---

### Post by XG4GRhE on 2013-08-05
> **steeldriver said:**
> Hello and welcome to the forum

Are you sure you're not just mistyping the filename? it should be /etc/host**s** , if you type a filename that doesn't already exist then gedit will open a blank file

Also you should use gksudo not plain sudo for GUI applications

```
**gk**sudo gedit /etc/host**s**
```

Oh yup, you're right I was doing /etc/host instead of /etc/hosts

thanks bro

---

