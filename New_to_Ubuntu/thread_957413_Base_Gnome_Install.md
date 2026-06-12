---
title: "Base Gnome Install"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by kineem on 2008-10-24
Hello. I have installed Ubuntu server. Now I want to add gnome desktop to it. sudo apt-get install ubuntu-desktop will do but it gets too much software that are unnecessary for me. I want to install the minimal gnome. Could you post the terminal code for the task?

---

### Post by kpkeerthi on 2008-10-24
```
apt-get install gnome
```


[http://packages.ubuntu.com/hardy/gnome](http://packages.ubuntu.com/hardy/gnome)

---

### Post by Duck2006 on 2008-10-24
From the command prompt,

sudo aptitude install ubuntu-desktop

---

### Post by SuperSonic4 on 2008-10-24
> **Duck2006 said:**
> From the command prompt,

sudo aptitude install ubuntu-desktop

The OP doesn't want ubuntu-desktop installed.

I'd go with post 2 although gnome-core might be a package

---

### Post by kineem on 2008-10-24
> **kpkeerthi said:**
> ```
apt-get install gnome
```


[http://packages.ubuntu.com/hardy/gnome](http://packages.ubuntu.com/hardy/gnome)

I just installed the server. Will it retrieve all dependenies, too? I dont have x server or even gdm etc.

---

### Post by kpkeerthi on 2008-10-24
The link has dependencies it would pull.

---

### Post by kineem on 2008-10-24
> **kpkeerthi said:**
> The link has dependencies it would pull.

Terminal warned me as :

[PHP]
The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.20.2.2) but it is not going to be installed
[/PHP]


Now I  installed this:

> sudo apt-get install gnome-core gdm xorg

Is there anything to install? Now I can use desktop environment but with some problems.

---

